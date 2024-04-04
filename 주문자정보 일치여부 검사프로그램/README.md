# 주문자정보 일치여부 검사프로그램
## 주문정보를 지우면 에러메시지가 없어지도록 개선해야함
##
![image](https://github.com/ohseungheon/HTML_CSS_project/assets/132635759/f69e645f-c125-470d-baf3-56d62ac6fb48)


```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>주문 및 배송 정보</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }

        #container {
            width: 500px;
            padding: 20px;
            border-radius: 8px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        .section {
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 20px;
        }

        .section h2 {
            margin-bottom: 10px;
            font-size: 18px;
            color: #333;
        }

        .input-group {
            margin-bottom: 15px;
        }

        .input-group label {
            font-weight: bold;
            margin-bottom: 5px;
            display: block;
        }

        .input-group input {
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
            width: calc(100% - 16px);
        }

        .checkbox-label {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }

        .checkbox-label input[type="checkbox"] {
            margin-right: 10px;
        }

        form {
            background-color: #007bff;
            color: #fff;
            border: none;
            padding: 10px 0;
            border-radius: 4px;
            cursor: pointer;
            text-align: center;
            font-weight: bold;
        }

        form:hover {
            background-color: #0056b3;
        }

        #err {
            color: red;
            font-size: 10px;
        }
    </style>
</head>

<!-- <body>  <legend>좋아하는 과일</legend>
    <input type="checkbox" id="banana" name="fruits" value="banana">
    <label for="banana">바나나</label> -->
<div id="container">
    <div class="section">
        <h2>주문 정보</h2>
        <div class="input-group">
            <label for="order-name">이름:</label>
            <input type="text" class="orderInfo" id="order-name" name="order-name">
        </div>
        <div class="input-group">
            <label for="order-contact">연락처:</label>
            <input type="text" class="orderInfo" id="order-contact" name="order-contact">
        </div>
        <div class="input-group">
            <label for="order-address">주소:</label>
            <input type="text" class="orderInfo" id="order-address" name="order-address ">
        </div>
    </div>
    <div class="section">
        <div id="err"></div>
        <h2>배송 정보</h2>
        <div class="checkbox-label">
            <input type="checkbox" id="check" value="check">
            <label for="check">주문 정보와 동일합니다</label>
        </div>
        <div class="input-group">
            <label for="delivery-name">이름:</label>
            <input type="text" class="deliverInfo" id="delivery-name">
        </div>
        <div class="input-group">
            <label for="delivery-contact">연락처:</label>
            <input type="text" class="deliverInfo" id="delivery-contact">
        </div>
        <div class="input-group">
            <label for="delivery-address">주소:</label>
            <input type="text" class="deliverInfo" id="delivery-address">
        </div>
    </div>
    <form action="deliverPage.html" method="get" onsubmit="return f1() && f2()">
        <input type="submit" value="결제하기">
    </form>
</div>
<script>
    let flag = 0;
    const checkBtn = document.getElementById("check");
    const order = document.querySelectorAll(".orderInfo");
    const orderName = document.querySelector("#order-name");
    const orderContact = document.querySelector("#order-contact");
    const orderAddr = document.querySelector("#order-address");
    const deliver = document.querySelectorAll(".deliverInfo");
    const deliverName = document.querySelector("#delivery-name");
    const deliverContact = document.querySelector("#delivery-contact");
    const deliverAddr = document.querySelector("#delivery-address");
    const err = document.querySelector("#err")

    orderName.addEventListener("input", f3)
    deliverName.addEventListener("input", f3)
    orderContact.addEventListener("input", f3)
    deliverContact.addEventListener("input", f3)
    orderAddr.addEventListener("input", f3)
    deliverAddr.addEventListener("input", f3)


    checkBtn.addEventListener("click", function () {
        if (flag == 0) {
            for (let i = 0; i < order.length; i++) {
                deliver[i].value = order[i].value;
            }
            flag = 1;
        } else {
            for (let i = 0; i < order.length; i++) {
                deliver[i].value = "";
            }
            flag = 0;
        }
        f3()
    });


    function f1() {
        let null_check = 0;

        for (let i = 0; i < order.length; i++) {
            if (order[i].value == "") {
                null_check++;
            }

        }


        if (null_check != 0) {
            alert("주문정보를 모두 입력하세요")
            return false;
        } else {

            return true;
        }

    }



    function f2() {
        let null_check = 0;
        for (let i = 0; i < order.length; i++) {
            if (order[i].value !== deliver[i].value) {
                null_check++;
            }

        }

        if (null_check != 0) {
            null_check = 0
            alert("주문정보와 배송정보가 일치하지 않습니다 다시 확인하세요")
            return false
        }


    }




    function f3() {
        if (deliverName.value != ""||deliverContact.value!=""||deliverAddr.value!="") {
            if (orderName.value !== deliverName.value ||
                orderContact.value !== deliverContact.value ||
                orderAddr.value !== deliverAddr.value) {
                err.innerHTML = "주문정보와 배송정보가 일치하지 않습니다 다시 확인하세요";
            } else {
                err.innerHTML = ""; // 일치할 때 메시지를 지움
            }
        }else{ err.innerHTML = "";}
    }


</script>
</body>

</html>
```
