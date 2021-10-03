# Database

A collection of data stored in a computer system

## Relational database 
A database that contains a series of related tables
- A database that contains a series of tables that can be connected to show relationships.

## Primary key

An identifier that references a column in which each value is `unique`.

## Foreign key

A field within a table that's a primary key in another table.
- A column or group of columns in a relational database table that provides a link between the data and two tables.
- Refers to the field in a table that's the primary key of another table.
- More than one foreign key is allowed to exist in a table. 

# Metadata

Meta
- Usually they're talking about something referencing back to itself or being completely self aware.
- Tự reference tới chính nó
    - Data analyst phân tích về việc data analysis
    - Data về data
    
Metadata
- Data about data
- Metadata is an abstract concept

Metadata tells you 
- where the data comes from
- when and how it was created
- what it's all about.

Metadata is used in database to help data analysts interpret the contents of the data within a database.
- Metadata tóm tắt content của data

Metadata also makes data more reliable by making sure it's 
- accurate: sự chính xác
- precise: nội dung tóm tắt
- relevant: sự liên quan
- timely: mang tính thời đại

Metadata creates a single source of truth by keeping things consistent and uniform. 
- Metadata = xương sống do giữ mọi thứ
    - nhất quán, trước sau như một
    - thống nhất, xác định 1 standard chung

Dựa vào metadata có thể xác định được data đã clean hay chưa
- Tạo ra standard để có thể sử dụng external data từ bên ngoài vào project

Metadata is stored in a single, central location and it gives the company standardized information about all of its data. 

## Type of Metadata

### Descriptive: Mô tả

Metadata that describes a piece of data and can be used to identify it at a later point in time.
- Data làm nhãn mác cho một khối data khác trong khoảng thời gian gần nhất
- Metadata có thể không bao giờ hết hạn
- ID numbers = Descriptive Metadata

### Structural: Cấu trúc

Metadata that indicates how a piece of data is organized and whether it's part of one, or more than one, data collection.
- Data làm mục lục cho một khổi data khác
- Chỉ ra cấu trúc của data collection ➝ hướng dẫn cách để tìm tới một data cụ thể

### Administrative: Quản lý

Metadata that indicates the technical source of a digital asset.
- Là thông số kĩ thuật cho asset kĩ thuật số

## Metadata repository

A database specifically created to store metadata.
- Describe the state and location of the metadata
- Describe the structure of the tables inside
- Describe how data flows through the repository
- Keep track of who accesses the metadata and when

Metadata repositories make it easier and faster to bring together multiple sources for data analysis. 
- Bring together multiple sources of data
- Verify that data from an outside source is being used appropriately 
- Confirm how or when data was collected

## Data governance: Quản lý data

A process to ensure the formal management of a company’s data assets.

# Data Sources

## Comma-Separated Values (CSV): Giá trị được phân tách bằng dấu phẩy

File lưu trữ data với value được phân tách = dấu phẩy + xuống dòng
- A CSV file saves data in a table format

A CSV file makes it easier for data analysts to 
- Examine a small subset of a large dataset
- Import data to a new spreadsheet
- Distinguish values from one another

## Sorting & Filtering Data

Sorting involves arranging data into a meaningful order to make it easier to understand, analyze, and visualize.
- Sort = tổ chức data theo một thứ tự có ý nghĩa
- ➝ Nghĩ lý do trước khi sort

# Organizing & Protecting data

## Naming conventions

Consistent guidelines that describe the content, date, or version of a file in its name.
- Guideline cho đặt tên file để tóm tắt content + date + version.
- Use logical and descriptive names for your files to make them easier to find and use.

Work out and agree on file naming conventions early on in a project to avoid renaming files again and again.
- Thảo luận ➝ đồng thuận 1 naming conventions

Align your file naming with your team's or company's existing file-naming conventions.
- Tuân theo Naming conventions của công ty

Ensure that your file names are meaningful
- File name phải ý nghĩa
- Consider including information like project name and anything else that will help you quickly identify (and use) the file for the right purpose.

Include the date and version number in file names; common formats are YYYYMMDD for dates and v## for versions (or revisions).
- Nên có thêm date + version cho file

Create a text file as a sample file with content that describes (breaks down) the file naming convention and a file name that applies it.
- Tạo ra 1 sample file để mọi người tuân theo

Avoid spaces and special characters in file names. Instead, use dashes, underscores, or capital letters. Spaces and special characters can cause errors in some applications.
- Tránh kí tự đặc biệt trong filename, chung 1 format cho tất cả các name

## Foldering

Organizing files into folders helps keep project-related files together in one place. 
- Break folders down into subfolders

Breadcrumb là một công cụ tổ chức files + folder hữu hiệu
- Nó có thể trở thành một câu chuyện nếu đc dùng đúng cách
    - VD: Finances/Payroll/:year/:month-number-:month-text/:date-:man.sheet
    - Finances/Payroll/2021/3-March/20-John.sheet

Create folders and subfolders in a logical hierarchy so related files are stored together.

Separate ongoing from completed work so your current project files are easier to find. Archive older files in a separate folder, or in an external storage location.

If your files aren't automatically backed up, manually back them up often to avoid losing important work.

## Archiving older files

Move old projects to a separate location to create an archive and cut down on clutter

## Align your naming and storage practices with your team

## Develop metadata practices
