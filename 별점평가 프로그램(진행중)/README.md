# 별점평가 프로그램
![image](https://github.com/ohseungheon/TIL/assets/132635759/3a110819-cac7-4695-a0aa-abe37515a579)
```html

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        li {
            display: inline;
        }

        .chk {
            display: none;
        }

        .star-label {
            display: inline-block;
            width: 40px;
            height: 40px;
            background-image: url("../emptystar.PNG");
            background-size: cover;
            cursor: pointer;

        }


        .chk:checked+.star-label {
            background-image: url('../fillstar.PNG');
        }
    </style>
    <script src="https://code.jquery.com/jquery-3.7.1.js"
        integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"></script>
</head>

<body>
    <div id="wrap">
        <ul>
            <li><input type="checkbox" class="chk" id="chk1"><label class="star-label" for="chk1"></label></li>
            </li>
            <li><input type="checkbox" class="chk" id="chk2"><label class="star-label" for="chk2"></label></li>
            </li>
            <li><input type="checkbox" class="chk" id="chk3"><label class="star-label" for="chk3"></label></li>
            </li>
            <li><input type="checkbox" class="chk" id="chk4"><label class="star-label" for="chk4"></label></li>
            </li>
            <li><input type="checkbox" class="chk" id="chk5"><label class="star-label" for="chk5"></label></li>
            </li>
        </ul>
    </div>

    

    <script>

        let beforeidx = 0;
        let start = 0;
        const chks = document.querySelectorAll(".chk");
        chks.forEach(chk => {
            chk.addEventListener("click", checkCount);
        });

        function checkCount(e) {
            console.log("test");
            console.log(event.target);
            console.log(Array.from(chks).indexOf(event.target));

            idx = Array.from(chks).indexOf(event.target);

            if (start === 0) {
                for (let i = 0; i < idx; i++) {
                    chks[i].checked = true
                }
                start = 1

            } else if (beforeidx == idx) {
                for (let i = 0; i <= idx; i++) {
                    chks[i].checked = true
                }
            } else {
                for (let i = 0; i < chks.length; i++) {
                    chks[i].checked = false;

                }
                for (let i = 0; i <= idx; i++) {
                    chks[i].checked = true
                }

            }
            beforeidx = idx;
            console.log(beforeidx)
            idx = 0;




        }
    </script>
</body>

</html>


```
