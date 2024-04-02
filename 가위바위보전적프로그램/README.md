# 컴퓨터와 가위바위보 프로그램

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>가위바위보 게임</title>
    <style>
        .container2 {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border: solid 1px black;
            padding: 10px;
            width: 750px;
            height: 700px;
            margin: auto;
        }

        li {
            list-style-type: none;
            display: inline-block;
            width: 45%;
        }

        div {
            border: solid 1px black;
            text-align: center;
            margin-top: 10px;
            padding: 10px;
        }

        #result {
            background-color: aquamarine;
            text-align: center;
            font-size: 30px;
            padding: 10px;
            width: 100%;
        }
        #score {
            background-color: rgb(89, 146, 233);
            text-align: center;
            font-size: 30px;
            padding: 10px;
            width: 100%;
        }

        #highScore {
            background-color: rgb(230, 115, 20);
            text-align: center;
            font-size: 30px;
            padding: 10px;
            width: 100%;
        }

        #title {
            font-size: 50px;
            text-align: center;
            margin-bottom: 20px;
        }

        #btn {
            width: 200px;
            height: 50px;
            font-size: 20px;
        }

        input[type="radio"] {
            display: none; /* 라디오 버튼 기본 스타일 숨기기 */
        }

        input[type="radio"] + label {
            display: inline-block;
            background-color: #f0f0f0;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            margin: 5px;
        }

        input[type="radio"]:checked + label {
            background-color: #90ee90; /* 선택된 라디오 버튼 스타일 변경 */
        }

        input[type="radio"] + label:hover {
            background-color: #d3d3d3; /* 호버 시 스타일 변경 */
        }

        img {
            width: 200px;
        }

        ul {
            width: 500px;
        }
    </style>
</head>

<body>
<div class="container2">
    <div id="title">가위바위보 게임</div>
    <ul class="container">
        <li>
            <img src="../../math_img_1.jpg" id="userimg">
        </li>
        <li>
            <img src="../../math_img_2.jpg" id="comimg">
        </li>
    </ul>
    <div>
        <input type="radio" id="option1" name="option" value="1">
        <label for="option1">가위</label>

        <input type="radio" id="option2" name="option" value="2">
        <label for="option2">바위</label>

        <input type="radio" id="option3" name="option" value="3">
        <label for="option3">보</label>

        <button id="btn" onclick="f()">실행</button>
    </div>
    <div id="result">옵션을 선택해주세요</div>
    <div id="score">score: 0점</div>
    <div id="highScore">최고 기록 score: 0점</div>
</div>

<script>
    let wincount = 0;
    let losecount = 0;
    let drawcount = 0;
    let score =0;
    let highScore=0;
    let count =0
    let winrate=0;
    let count1 =0;
    let count2 =0;
    let count3 =0;
    let wincount1 = 0;
    let wincount2 = 0;
    let wincount3 = 0;

    const btn = document.getElementById("btn");
    const result = document.getElementById("result");

    btn.addEventListener("click", f);

    function f() {
        btn.removeEventListener("click", f);
        count++
        const selectedOption = document.querySelector('input[name="option"]:checked');
        if (!selectedOption) {
            result.innerText = "옵션을 선택해주세요.";
            return;
        }
        const inputValue = selectedOption.value;

        let rdNum2 = Math.floor(Math.random() * 3 + 1);
        let comInput = rdNum2;

        const userimg = document.getElementById("userimg");
        const comimg = document.getElementById("comimg");

        userimg.setAttribute("src", `../../math_img_${inputValue}.jpg`);
        comimg.setAttribute("src", `../../math_img_${rdNum2}.jpg`);

        if (inputValue == comInput) {
            
            drawcount++;
            result.innerText = `${count}전 ${wincount}승 ${drawcount}무 ${losecount}패(승률:${winrate}) 비겼습니다`;
            result.style.backgroundColor = "aquamarine";
            document.querySelector("#score").innerHTML = "score "+`${score}`+"점"
        } else if ((inputValue == 1 && comInput == 3) || (inputValue == 2 && comInput == 1) || (inputValue == 3 && comInput == 2)) {
            wincount++;
            // if (selectedOption.value==1){
            //     wincount1++
            // }else if(selectedOption.value==2){

            // }
            score =score+10
            winrate=(wincount/count)*100
            winrate = winrate.toFixed(1);
            result.innerText = `${count}전 ${wincount}승 ${drawcount}무 ${losecount}패(승률:${winrate}) 이겼습니다`;
            result.style.backgroundColor = "lightgreen";
            document.querySelector("#score").innerHTML = "score "+`${score}`+"점"
        } else {
            losecount++;
            score =score-10
            result.innerText = `${count}전 ${wincount}승 ${drawcount}무 ${losecount}패(승률:${winrate}) 졌습니다`;
            result.style.backgroundColor = "salmon";
            document.querySelector("#score").innerHTML = "score "+`${score}`+"점"
        }
        if (score>=highScore){
            highScore =score
            document.querySelector("#highScore").innerHTML = "최고기록 "+`${highScore}`+"점"

        }
    }
</script>
</body>
</html>

```
