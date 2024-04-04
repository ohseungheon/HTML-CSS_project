# 드라마 회차선택 체크박스
![image](https://github.com/ohseungheon/HTML_CSS_project/assets/132635759/7b41dd4f-bd65-46f5-a972-c2ad8833c362)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        #wrap {
            width: 150px;
        }

        ul {
            padding: 0;
            margin: 0;
        }

        li {
            margin-bottom: 10px;
        }

        label {
            cursor: pointer;
        }

        input[type="checkbox"] {
            margin-right: 5px;
        }
    </style>
</head>

<body>
    <div id="wrap">
        <ul>
            <li>
                <input type="checkbox" class="chk_all" id="all">
                <label for="all">전체 회차선택</label>
            </li>
            <li>
                <input type="checkbox" class="chk" id="item1">
                <label for="item1">1화</label>
            </li>
            <li>
                <input type="checkbox" class="chk" id="item2">
                <label for="item2">2화</label>
            </li>
            <li>
                <input type="checkbox" class="chk" id="item3">
                <label for="item3">3화</label>
            </li>
            <li>
                <input type="checkbox" class="chk" id="item4">
                <label for="item4">4화</label>
            </li>
            <li>
                <input type="checkbox" class="chk" id="item5">
                <label for="item5">5화</label>
            </li>
        </ul>
    </div>

    <script>
        let remainFalseCheck = true
        let result = 0
        let count = 0;
        let allChecked = false
        const chkAll = document.querySelector(".chk_all");
        const chks = document.querySelectorAll(".chk");
        for (let i = 0; i < chks.length; i++) {
            chks[i].addEventListener("click", checkCount)

        }



        chkAll.addEventListener("click", () => {
            chks.forEach(element => {
                element.checked = chkAll.checked;
            });
            //console.log(chkAll.checked);


            if (!allChecked) {
               
                allChecked = true;
            } else {

                
                allChecked = false;
            }
            console.log(allChecked);
            console.log(count)
        });


        function checkCount() {
            // 쭉돌면서 true이면 카운트에 넣고
            //카운트가 4면 allcheck에 트루
            for (let i=0; i < chks.length; i++) {
                if (chks[i].checked) {
                    count++;
                }
            }

            console.log(count);
            if (count==5){
                chkAll.checked=true;
                allChecked = true;
            }

            if(allChecked&&count<5){
                chkAll.checked=false;
                allChecked = false;
            }
            count=0;
        }
    </script>
</body>

</html>
```
