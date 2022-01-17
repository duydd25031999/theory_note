# Container
Ứng dụng sẽ chạy trên một môi trường cách ly là container
- Có thể coi container = máy ảo
- Container nhẹ hơn máy ảo (do ít lớp hơn)
- Khi 1 image chạy => sinh ra 1 container -> sinh ra container name
    - containerName = new ImageName();
    - Khi cài đặt thêm option vào container => không ảnh hưởng iamge gốc

`docker ps`: List các container đang chạy

`docker ps -a`: List các container đã + đang chạy 

`docker start container_name`: start lại container

`docker attach container_id/container_name`: tương tác với container đang chạy

`docker exec container_id/container_name command` = `docker attach container_id/container_name` + run `command` in container + `exit`

`docker stop container_id/container_name`: dừng container đang chạy

`docker rm container_id/container_name`: xóa container đã dừng

`docker rm container_id/container_name -f`: xóa container đang chạy

`docker commit container_id/container_name new_image_name:new_image_tag`: chuyển container => image

`docker save --output file_name.tar image_id`: export image to file

`docker load -i file.tar`: import file to image
- nhưng chưa có name + tag
- chỉ có id

`docker tag image_id name:tag`: đổi name + tag của image

`docker restart container_id/container_name` restart container

# Image
Phần mềm được đóng gói trong docker
- Ví dụ
    - Image: PHP
    - Image: Nginx
    - Image: MySQL
- Chỉ có thể đọc | chạy
- Không thể sửa đổi
- Container sẽ chạy các images
- Giống npm
- Tải image

    `docker pull image_name:tag`

- Remove image

    `docker image rm image_name:tag`

    `docker image rm image_id`

Chạy 1 image = tạo container

`docker run -option_docker image_id command_image -option_command_image`
- `--interactive`, `-i`
    - Keep STDIN open even if not attached
    - Giữ cho Container nhận input dù ko bật `attach`
- `--tty`, `-t`
    - Allocate a pseudo-TTY
    - Phân bổ TTY giả
- `--volume`, `-v`
    - Ánh xạ vào 1 folder của host | container khác
    - `docker run -v folder_source_path:folder_path_map image_id`: map folder_source_path đến folder_path_map trong container
    - Khi thực hiện bất kì tương tác nào trong mapping folder ở 2 môi trường thì đều sync với nhau
- `--detach`, `-d`
    - Run container in background and print container ID
    - Chạy docker trong background
- `--volumes-from`
    - Ánh xạ Volume tới 1 container khác đang chạy
- `--name`
    - Đặt tên cho Container
    - `docker run --name "container_name" image_id`: tạo container với tên
- `--mount`
    - Attach a filesystem mount to the container
    - Kết nối 1 filesystem tới container
    - `docker run -it --mount source=volume_name,target=image_path image`
- `--rm`		
    - Automatically remove the container when it exits
- `--publish`, `-p`		
    - Publish a container's port(s) to the host
    - Map 1 port container tới 1 port của host
    -  `docker run -it -p host_port:container_port image`
- `--network`	
    - kết nối container tới 1 network
    -  `docker run --network network_name image`
- `--environment VAR_NAME=VALUE`, `-e`	
    - kết nối container tới 1 network
    -  `docker run -e VAR_NAME=VALUE image`

# Volume
Ổ đĩa của 1 container
- Có thể tạo 1 volume độc lập với container
- Khi remove container thì volume có thể không bị xóa

`docker volume ls`: List all volume đang tồn tại

`docker volume create -option volume_name`: create volume
- `--opt`, `-o`		
    - Set driver specific options
        - `device`: path map tới folder ở host
        - `type`: lại volume
        - `o`: option
    
    `volume create --opt device=folder_path --opt type=none --opt o=bind volume_name`: tạo 1 volume map tới 1 folder ở host

`docker volume inspect volume_name`: xem infor của 1 volume

`docker volume rm volume_name`: Remove volume

# Network
Kết nối giữa các container và ra bên ngoài
- Có 1 default bridge network để các container khởi tạo default connect tới net work đó
- 1 Container có thể connect nhiều network

`docker network ls`: list các network
- Type `bridge`: network giữa các container
    - Các container trong 1 network có thể kết nối với nhau
        - Có thể ping tới nhau
    - Nhưng chưa kết nối với bên ngoài network

`docker network create network_name`: tạo network
- `--driver`: loại network
    - `bridge`: cầu

`docker network network_name connect container_name`: kết nối network tới 1 container

`docker network inspect network_name`: xem infor của 1 network
- `Container`: các containers đang kết nối vào mạng này

# Docker-compose
Setup 1 kịch bản chạy docker
- Tạo các steps để setup docker cho 1 project


# Dockerfile
File config để tạo 1 image
- Image mới này = image source + setup cần thiết -> chỉ cần run + 1 ít setup

# MySQL
- Port: 3304
- Databases Folder: /var/lib/mysql
- Enviroment
    - MYSQL_ROOT_PASSWORD: root password
        - Cần phải setup
1. Run
    - `docker run -e MYSQL_ROOT_PASSWORD=PASS -v host_path:/var/lib/mysql --name container_name mysql`

# Httpd

Appache khi chạy sẽ nạp file cấu hình ở `/usr/local/apache2/conf/httpd.conf`
1. Chạy `docker run -rm -v host_folder_path:container_path httpd cp /usr/local/apache2/conf/httpd.conf container_path`: Copy file config từ image ra folder của host
1. Nạp các module để chạy php
    1. `LoadModule proxy_module modules/mod_proxy.so`
    1. `LoadModule proxy_scgi_module modules/mod_proxy_fcgi.so`
1. Thêm PHP Handler cho apache
    1. Thêm `AddHandler "proxy:fcgi://php_container_name:9000" .php` vào cuối file config
        - 9000 = default port của php
1. Đổi root folder cho apache
    1. `DocumentRoot "container_folder"`
    1. `<Directory "container_folder">`
1. Chạy httpd container
    - `docker run --network  --name c-httpd -p host_port:80 -p 443:443 -v host_folder_path:container_folder_path -v host_path/httpd.conf:/usr/local/apache2/conf/httpd.conf httpd`
    - 443: port chuyên lắng nghe HTTPS
    - 80: defailt port của httpd.conf `Listen 80`
        - Có thể đổi trong file httpd.conf

# Busybox
- Là một công cụ nhỏ gọn dựa trên linux
