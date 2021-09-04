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

Two way to make decision by data
1. data-driven decision making
1. data-inspired decision making
    - Explores different data sources to find out what they have in common
    - Data-inspired decision-making explores different data sources to find commonalities.

After analyzing data we started using an algorithm.
- An algorithm is a process or set of rules to be followed for a specific task.

Our analysis took data ➞ turned it into information by comparing it with other data.
- <ins tooltip title="hành cảnh, tình huống">Context</ins> is important.
- Knowledge = When we consume information, understand it, and apply it, that's when data is most useful.

There are limitations to data analytics. 
- Sometimes we don't have access to all of the data we need, o
- data is measured differently across programs, which can make it difficult to find concrete examples

When data is <ins tooltip title="diễn giải, xử lý">interpreted</ins> incorrectly, it can lead to huge losses. 
- Nếu hỏi câu hỏi sai mục tiêu 
    - ➞ phương hướng sai (yêu cầu sai)
    - ➞ collect sai data (dù làm đúng yêu cầu)
    - Example: Coke launch failure in 1985
- Không đồng bộ hệ quy chiếu + đơn vị đo
    - Hiểu sai data (dù làm đúng quy trình)

When data is used <ins tooltip title="được dùng một cách chiến lược, có kế hoạch">strategically</ins>, businesses can transform and grow their revenue.

Với data analyst, skills and knowledge be most important part
- Data chỉ là rác nếu không biết cách dùng
- keep a data-driven mindset
- ask lots of questions
- experiment with many <ins tooltip title="thử nghiệm nhiều khả năng khác nhau">different possibilities</ins>

different questions make different kinds of data

2 of all kinds of data
- <ins tooltip title="Định lượng">Quantitative</ins> data
    - specific and objective <ins underline>measures</ins> of <ins underline>numerical</ins> facts.
    - answer questions
        - the what
        - how many
        - how often
    - See data on numbers visualized
        - Chart
        - graphs
- <ins tooltip title="Định tính">Qualitative</ins> data
    - describes subjective or explanatory measures of qualities and characteristics or things that can't be measured with numerical data
        - measures qualities and characteristics
        - is subjective
    - answer questions
        - why quesion
    - more high-level understanding of why the numbers are the way they are
    - help add context to problem

Example: local ice cream shop's rating has been going down
- using their online reviews
1. Quantitative quesions: measurable questions
    - How many negative reviews are there? 
    - What's the average rating? 
    - How many of these reviews use the same keywords?
    - ➞ Numerical results that help confirm their customers <ins tooltip title="Không hài lòng">aren't satisfied</ins>.
    - Data tools
        - Structured interview
        - Surveys
        - Polls
1. Qualitative quesions
    - Why are customers unsatisfied? 
    - How can we improve their experience? 
    - ➞ Tìm điểm tương đồng trong data
        - Tìm được keyword chung trong các review tệ
    - Tiếp tục hỏi why để đào sâu hơn nguyên nhân
    - Data tools
        - Focus group
        - Social media text analysis
        - In-person review

Qualitative data can help analysts better understand their quantitative data by providing a reason or more thorough explanation
- quantitative data generally gives you the what, and qualitative data generally gives you the why

