# 날짜계산 프로그램
![image](https://github.com/ohseungheon/HTML_CSS_project/assets/132635759/9e03ccb7-a44d-412b-9895-bc209e0d3b98)


```html

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>우리 만난지 기념일 계산</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        .wrapper {
            max-width: 400px;
            margin: 20px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        .wrapper > div {
            margin-bottom: 10px;
        }

        ul {
            padding: 0;
        }

        li {
            font-weight: bold;
            list-style: none;
            margin-bottom: 5px;
            padding: 10px;
            display: flex;
            justify-content: space-between
        }

        #weMet {
            text-align: center;
            font-size: 14px;
        }
        
        #Line {
            
            font-size: 10px;
            background-color: rgb(88, 87, 88);
            color: white;
            padding: 5px 10px;
            border-radius: 5px;
        }
        
        span {
            font-size: 12px;
            text-align: right;
            font-weight: normal;
        }
        
        #date {
            font-weight: bold;
            text-align: center;
            font-size: 30px;
        }
    </style>
</head>

<body>
    <div class="wrapper">
        <div id="weMet">우리 만난지 </div>
        <div id="date"></div>
        <div id="Line"> 기념일 계산</div>
        <ul>
            <li id="date100">100일 <span></span></li>
            <li id="date200">200일 <span></span></li>
            <li id="date365">1년 <span></span></li>
            <li id="date500">500일 <span></span></li>
        </ul>
    </div>
    <script>
        const now = new Date();
        metDate = new Date('2024-02-15');

        const date1 = new Date('2024-02-15');
        const date2 = new Date('2024-04-03');
        const differenceInMilliseconds = Math.abs(date2 - date1);
        const millisecondsInDay = 1000 * 60 * 60 * 24;

        const differenceInDays = Math.floor(differenceInMilliseconds / millisecondsInDay);

        //100일
        const oneHundredDaysLater = new Date(date1);
        oneHundredDaysLater.setDate(oneHundredDaysLater.getDate() + 100);

        //200일
        const twoHundredDaysLater = new Date(date1);
        twoHundredDaysLater.setDate(twoHundredDaysLater.getDate() + 200);

        //1년
        const oneyearDaysLater = new Date(date1);
        oneyearDaysLater.setDate(oneyearDaysLater.getDate() + 365);

        //500일
        const fiveHundredDaysLater = new Date(date1);
        fiveHundredDaysLater.setDate(fiveHundredDaysLater.getDate() + 500);

        // 출력부분
        const date = document.getElementById("date");
        date.textContent = differenceInDays + "일";

        const date100 = document.getElementById("date100");
        const date200 = document.getElementById("date200");
        const date365 = document.getElementById("date365");
        const date500 = document.getElementById("date500");

        date100.querySelector("span").textContent = oneHundredDaysLater.getFullYear() + "년 " + (oneHundredDaysLater.getMonth() + 1) + "월 " + oneHundredDaysLater.getDate() + "일";
        date200.querySelector("span").textContent = twoHundredDaysLater.getFullYear() + "년 " + (twoHundredDaysLater.getMonth() + 1) + "월 " + twoHundredDaysLater.getDate() + "일";
        date365.querySelector("span").textContent = oneyearDaysLater.getFullYear() + "년 " + (oneyearDaysLater.getMonth() + 1) + "월 " + oneyearDaysLater.getDate() + "일";
        date500.querySelector("span").textContent = fiveHundredDaysLater.getFullYear() + "년 " + (fiveHundredDaysLater.getMonth() + 1) + "월 " + fiveHundredDaysLater.getDate() + "일";
    </script>
</body>

</html>


```
