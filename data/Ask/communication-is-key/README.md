<style>
[tooltip] {
    position: relative;
    padding-bottom: 0.25px;
    border-bottom: solid 1px;
    text-decoration: none;
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

# Clear communication

Before you communicate, think about
1. Who your audience is
1. What they already know
1. What they need to know
1. How you can communicate that effectively to them

- Example: Analyzing annual sales data, and you discover that all of the online sales data is missing.

    1. Who your audience is
        - In this case = connect to other data analysts + project manager + VP of sales

    1. What they already know

        - Other data analysts: know all the details about which data-set you are using already

        - Project manager: timeline you're working towards.

        - VP of sales: high-level goals of the project

    1. What they need to know
        
        - Other data analysts: 
            - know the details of where you have tried so far
            - any potential solutions you've come up with

        - Project manager:
            - Different teams that could be affected and the implications for the project
            - Especially if this problem changes the timeline.

        - VP of sales: there is anay potential issue that would delay or affect the project. 

    1. How you can communicate that effectively to them

        - Other data analysts + Project manager: 
            - Quickly book in a meeting with your project manager and fellow analysts
            - Let the team know about the missing online sales data and give them more background info.
            - Together, you discuss how this impacts other parts of the project. 
                - Come up with a plan and update the project timeline if needed
        
        - VP of sales: 
            -  Appreciate an e-mail update if there were changes to the timeline which your project manager might send along herself.

When you communicate thoughtfully and think about your audience first.
- You'll build better relationships and trust with your team members and stakeholders.
- Those relationships are key to the project's success and your own too.

# Effective communication

<ins tooltip title="vừa làm vừa học">Learn as you go</ins> and ask questions.
- Không ngại hỏi nếu không biết

Every work setting has some form of etiquette.
- Mỗi công việc nên có 1 cách thức để giao tiếp (1 quy định về lịch sự).

Practice good writing habits

Read your emails out loud
- Càng ngắn càng tốt
- Càng rõ ý, không cần dài dòng, đi thẳng vào vấn đề.

Answer in a timely manner as well
- Trả lời kịp thời.

# Balancing expectations and realistic project goals

Set a REASONABLE and REALISTIC timeline for the project.
- Sharing a high-level schedule with stakeholders so they can plan accordingly
- Creating a schedule with project phases and their approximate start dates
- Communicating clearly with the project manager and other team members

The earlier you can flag problems, the better.
- Không cần detail, chỉ cần chỉ ra là được.

Set realistic expectations at every stage of the project.

1. Luôn setting kì vọng cho mọi thứ đang diễn ra.
1. Mình phải đưa ra cam kết với stakeholders là mình sẽ dự lại đc stories từ data
    ```
    SAi LẦM: Sometimes people think that data can answer everything and sometimes we have to acknowledge that that is simply untrue.
    ```
1. Đặt ra giả thuyêtts từ những data hiện có để có thể collect tiếp data cần thiết
    - Collect thêm loại data khác chỉ khi có giả thiết từ data cũ

# The data tradeoff: Speed versus accuracy: Tốc độ VS Chính xác

Chỉ tập trung vào tốc độ ➞ bỏ lỡ all stories ➞ không đạt được best answer
- Thưởng do bị bế tắc ➞ cản trở timeline ➞ cuống ➞ để cảm xúc chen lấn ➞ đưa ra answer chủ quan hóa
- Sử lý = cách pause ➞ sắp xếp lại quesions ➞ chia nhỏ problem ➞ new insights ➞ xin thêm time ➞ tiếp tục

1. Put the data in context, and find the story it’s telling
1. A data analyst reframes a question. 
1. They outline 
    - problem
    - challenges
    - potential solutions
    - timeframe. 

**REMEMBER**: luôn có bad news để gánh chịu
- Có thể ít hoặc nhiều
- Có thể nặng hoặc nhẹ
- Điều đó là tự nhiên 🠔 ko có mới bất tự nhiên
    - Cần có bước ngoặt để mở rộng tầm nhìn ➞ more insight
- Vì thế nên cần communicates ➞ nhận đc help phù hợp + nhanh chóng ➞ giải quyết bế tắc 🠔 ko biến mình thành nạn nhân

# Limitations of data

## The case incomplete (or nonexistent) data

have incomplete or nonexistent data 
- ➞ don't have enough data to reach a conclusion 
- ➞ solving a different problem altogether! 

## Don't miss misaligned data

collecting data from other teams + using existing spreadsheets 🠔 keep in mind that people use different business rules
- Quy hết các rule về cùng 1 hệ quy chiếu ➞ Tạo hệ quy chiếu phải đảm bảo thỏa mãn các rules

## Deal with dirty data

Dirty data refers to data that contains errors.
- A good data cleaning effort can help you avoid this.

## Tell a clear story

1. Compare the same types of data:
    - Data can get mixed up when you chart it for visualization. 
    - Be sure to compare the same types of data and double check that any segments in your chart definitely display different metrics. 

1. Visualize with care: 
    - A 0.01% drop in a score can look huge if you zoom in close enough. To make sure your audience sees the full story clearly, it is a good idea to set your Y-axis to 0.

1. Leave out needless graphs: 
    - If a table can show your story at a glance, stick with the table instead of a pie chart or a graph. 
    - Your busy audience will appreciate the clarity.
    - Xem table đã đủ để tell story chưa?
        - Rồi ➞ để nguyên ➞ làm cái khác
        - Chưa ➞ mới nghĩ a pie chart or a graph 🠔 đừng nghĩ a pie chart or a graph từ đầu

1. Test for statistical significance: 
    - Sometimes two datasets will look different, but you will need a way to test whether the difference is real and important. 
    - So remember to run statistical tests to see how much confidence you can place in that difference.

1. Pay attention to sample size: 
    - Gather lots of data. 
    - If a sample size is small, a few unusual responses can skew the results. 
    - If you find that you have too little data, be careful about using it to form judgments. 
    - Look for opportunities to collect more data, then chart those trends over longer periods.

## Be the judge

Does your analysis answer the original question?

Are there other angles you haven't considered?
- Có những góc độ khác mà bạn chưa xem xét?

Can you answer any questions that may get asked about your data and analysis?

To make sure that a few unusual responses don’t skew results or lead to inaccurate judgements, a data analyst focuses on what element of the data collection? 
- Sampple size
