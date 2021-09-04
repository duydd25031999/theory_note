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

# Mathematical thinking
There are a lot of factors to consider when choosing the most helpful tool for your analysis.
- decide which tool to use is by the size of your dataset

# Small data
Made up of datasets concerned with specific metrics over a short, well defined period of time.
- Được tạo thành từ các tập dữ liệu liên quan đến các metrics cụ thể trong một khoảng thời gian ngắn, được xác định rõ ràng.
- Really small
- Specific
- Short <ins tooltip title="khoảng thời gian">time-period</ins>
- Make day-to-day decision

- Doesn't have a huge impact on bigger frameworks 
    - business operations.
- Use <ins underline>spreadsheets</ins> 
    - to organize and analyze smaller datasets

# Big data

## Defination

Larger & less specific datasets 
- Covering a longer period of time.
- Have to be broken down to be analyzed
- Useful for looking at large-scale questions and problems
- help companies make big decisions.
- switch to <ins underline>SQL</ins>
    - When you're working with data on this larger scale

## Compare
main differences between big and small data
- Small data is specific and concerns a short time period. Big data is less specific and concerns a longer time period.

|  | Small data | Big data |
|---|---|---|
| Define | Describes a data set made up of specific metrics over a short, well-defined time period | Describes large, less-specific data sets that cover a long time period |
| Tool | Usually organized and analyzed in spreadsheets | Usually kept in a database and queried |
| Size | Likely to be used by small and midsize businesses | Likely to be used by large organizations |
| Operation | Simple to collect, store, manage, sort, and visually represent | Takes a lot of effort to collect, store, manage, sort, and visually represent |
| Status | Usually already a manageable size for analysis | Usually needs to be broken into smaller pieces in order to be organized and analyzed effectively for decision-making |

## Challenges

A lot of organizations deal with data overload and way too much unimportant or irrelevant information.
- Có quá nhiều raw data
- Nhưng data lại không quan trọng || không liên quan tới mục tiêu

Important data can be hidden deep down with all of the non-important data, which makes it harder to find and use.
- Data có giá trị bị giấu quá sâu
- This can lead to slower and more inefficient decision-making time frames.

The data you need isn’t always easily accessible. 

Current technology tools and solutions still struggle to provide measurable and reportable data.
- tools + solution (của data enginer) vô dụng khi measurable and reportable data
- This can lead to unfair algorithmic bias. 

There are gaps in many big data business solutions.
- Có lỗi hổng trong solution cho big data

## Benefits

When large amounts of data can be stored and analyzed, it can help companies identify more efficient ways of doing business and save a lot of time and money.
- Càng nhiều data CÓ GIÁ TRỊ ➞ càng dễ tạo solution ➞ đỡ tốn time + money

Big data helps organizations spot the trends of customer buying patterns and satisfaction levels, which can help them create new products and solutions that will make customers happy.
- Tìm ra trend ➞ cải tiến ➞ nâng cao chất lượng 

By analyzing big data, businesses get a much better understanding of current market conditions, which can help them stay ahead of the competition.
- Thấu hiệu sự vận hành vi mô ➞ big picture

As in our earlier social media example, big data helps companies keep track of their online presence—especially feedback, both good and bad, from customers. 
- This gives them the information they need to improve and protect their brand.

## The three (or four) V words for big data

Volume: dung tích
- The amount of data

Variety: Sự đa dạng
- The different kinds of data

Velocity: Tốc độ
- How fast the data can be processed

Veracity: Tính xác thực
- The quality and reliability of the data
