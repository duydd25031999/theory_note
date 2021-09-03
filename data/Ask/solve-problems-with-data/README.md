<style>
[tooltip] {
    position: relative;
    padding-bottom: 0.25px;
    border-bottom: solid 1px
}

[tooltip]::before {
    display: none;
    content: attr(title);
    background-color: #6fa2fa;
    justify-content: center;
    border-radius: 3px;
    width: max-content;
    position: absolute;
    bottom: 100%;
    left: 50%;
    transform: translateX(-50%);
    text-align: center;
    padding: 0.25rem;
    max-width: 160px;
    word-break: keep-all;
    font-size: 0.75rem;
}

[tooltip]:hover::before {
    display: block;
}

[underline] {
    padding-bottom: 0.25rem;
    border-bottom: solid 1px;
    text-decoration: none;
}
</style>

# The six data analysis phases

## <ins underline>Sep 1</ins>: Ask

It’s impossible to solve a problem if you <b tooltip title="tìm ra phương hướng đúng cho project = đặt đúng câu hỏi">don’t know what it is</b>. These are some things to consider:
1. Define the problem you’re trying to solve 
1. Make sure you fully understand the stakeholder’s expectations
1. Focus on the actual problem and avoid any <b tooltip title="thứ gây nhiễu">distractions</b>
1. Collaborate with stakeholders and keep an open line of communication
1. Take a step back and see the whole situation in context

Questions to ask yourself in this step: 
1. What are my stakeholders saying their problems are?
1. Now that I’ve identified the issues, how can I help the stakeholders resolve their questions?

## <ins underline>Sep 2</ins>: Prepare
You will decide <b tooltip title="Thu thập raw data">what data you need to collect</b> in order to answer your questions and how to organize it so that it is useful. You might use your business task to decide: 
1. What <b tooltip title="field nào cần để đo">metrics</b> to measure
1. Locate data in your database
1. Create security measures to protect that data

Questions to ask yourself in this step: 
1. What do I need to figure out how to solve this problem?
1. What research do I need to do?

## <ins underline>Sep 3</ins>: Process

<b tooltip title="Clean data để data trở nên có giá trị, không rác">Clean data</b> is the best data and you will need to clean up your data to get rid of any possible errors, inaccuracies, or inconsistencies. This might mean:

1. Using <b tooltip title="tìm lỗi trong quá trình nhập data">spreadsheet</b> functions to find incorrectly entered data 
1. Using <b tooltip title="tìm những ô trống hoặc giá trị không có nghĩa">SQL</b> functions to check for extra spaces
1. Removing <b tooltip title="loại bổ những ô lặp">repeated entries</b>
1. Checking as much as possible for <b tooltip title="tìm các dự kiến có thể tìm ra trong data">bias</b> in the data

Questions to ask yourself in this step: 
1. What data errors or inaccuracies might get in my way of getting the best possible answer to the problem I am trying to solve?
1. How can I clean my data so the information I have is more consistent?

## <ins underline>Sep 4</ins>: Analyze

You will want to think <b tooltip title="Phân tích data để ra kết luận">analytically about your data</b>. At this stage, you might sort and format your data to make it easier to: 
1. Perform calculations
1. Combine data from multiple sources
1. Create tables with your results

Questions to ask yourself in this step:
1. What story is my data telling me?
1. How will my data help me solve this problem?
1. Who needs my company’s product or service? What type of person is most likely to use it?

## <ins underline>Sep 5</ins>: Share
Everyone <b tooltip title="Chia sẻ kết quả mỗi kiểu cho mỗi loại thính giả">shares their results differently</b> so be sure to summarize your results with clear and enticing visuals of your analysis using data viz tools like graphs or dashboards. This is your chance to show the stakeholders you have solved their problem and how you got there. Sharing will certainly help your team:  
1. Make better decisions
1. Make more informed decisions
1. Lead to stronger outcomes
1. Successfully communicate your findings

Questions to ask yourself in this step:
1. How can I make what I present to the stakeholders engaging and easy to understand?
1. What would help me understand this if I were the listener?

## <ins underline>Sep 6</ins>: Act
Now it’s time to <b tooltip title="Tư vấn cho thính giả về hành động dựa trên kết quả">act on your data</b>. You will take everything you have learned from your data analysis and put it to use. This could mean providing your stakeholders with recommendations based on your findings so they can make data-driven decisions.

Questions to ask yourself in this step:
1. How can I use the feedback I received during the share phase (step 5) to actually meet the stakeholder’s needs and expectations?

##  Structured thinking
Là quá trình data analysis thông qua 6 bước trên. Quá trình này sẽ có 4 hành động chính cho mỗi step:

1. Recognizing the current problem or situation
1. Organizing available information 
1. Revealing gaps and opportunities
1. Identifying your options

# Common problem types

- Có 6 common problem types

## Making predictions: Dự đoán
This problem type involves using data to make an informed decision about how things may be in the future.
- Dùng data để dự đoán những thứ sẽ diễn ra

## Categorizing things: Phân loại
This means assigning information to different <b tooltip title="nhóm: items có quan hệ với nhau">groups</b> or <b tooltip title="cụm: items gần nhau trên đồ thị">clusters</b> based on common features.
- Là phân loại  dựa trên data của chúng
    - Phân loại sản phẩm hot: thế nào được coi là hot, mức độ hot được measure bằng đại lượng nào, ...

## Spotting something unusual: Phát hiện điều gì đó bất thường
Identify data that is different from the <b tooltip title="bình thường, qui tắc">norm</b>
- Tìm nguồn gốc của điểm lạ thường dựa trên data.

## Discovering connections: 
Find similar challenges faced by different entities, and then combine data and insights to address them. 
- Tìm những thách thức tương tự mà các thực thể khác nhau phải đối mặt, sau đó kết hợp (data + insignht) để address chúng.
- Tìm connection = challenges tương tự nhau + insight + data
    - Categorization = tìm điểm tương đồng trong data
    - Connections = tìm điểm tương đồng trong challenges = deeper categorization

## Identifying themes: Xác đinh chủ đề
Takes categorization as a step further by grouping information into broader concepts
- Phân loại nâng cao = group information với concepts rộng hơn
- Categorizing things level 2
- Bắt buộc phân loại thành group
    - Tìm ra điểm liên quan của item
    - Từ điểm liên quan đó xác định ra 1 khái niệm
- Từ khái niệm đó thì dự đoán trong tương lại bất kì item nào thỏa mãn khái niệm đó thì sẽ thuộc nhóm này

Identifying themes = Categorizing things + Discovering connections

## Finding patterns
Using <b tooltip title="lịch sử của internal problem">historical</b> data to understand what happened in the past and is therefore likely to happen again.
- Sử dụng historical data để tìm ra sự tương đồng của của các sự kiện xuyên suốt history
- Từ đó xác định mẫu của sự kiện để dự đoán tương lai