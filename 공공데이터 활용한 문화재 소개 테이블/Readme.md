# 문화재 소개 테이블

![image](https://github.com/ohseungheon/HTML_CSS_project/assets/132635759/41676567-eed5-4851-a1e1-8958b0f22c93)

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 이미지를 감싸는 테두리 및 그림자 효과 */
        .image-wrapper {
            border: 4px solid #fff;
            border-radius: 50%;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }

        /* 테이블 헤더의 배경색 및 글꼴 변경 */
        th {

            
            /* border: solid 1px red; */
            background-color: #e2e0df;
            /* 오렌지색 배경 */
            color: #000000;
            /* 흰색 텍스트 */
            font-family: 'Arial Black', sans-serif;
            /* 글꼴 변경 */
            text-align: center;
        }

        /* 테이블 테두리를 둥글게 만듦 */
        table {
            border-radius: 15px;
        }

        /* 추가적인 텍스트 스타일 */
        .fancy-text {
            font-size: 18px;
            /* 폰트 크기 조정 */
            text-transform: uppercase;
            /* 대문자 변환 */
        }


        .scrollable {
            max-height: 20px;
            /* 스크롤이 표시될 최대 높이 */
            overflow-y: auto;
            /* 세로 스크롤을 표시 */
        }
    </style>
</head>

<body>
    <table>
        <button id="btn">데이터전송</button>
        <thead>
            <tr id="th">
                <!-- 여기에 테이블 헤더 내용을 추가하세요 -->
            </tr>
        </thead>
        <tbody>
            <!-- 각 행을 감싸는 div 요소에 스크롤 효과를 적용합니다 -->

            <tr id="data1" class=scrollable>
                <!-- 여기에 첫 번째 행 내용을 추가하세요 -->
            </tr>
            <tr id="data2">
                <!-- 여기에 두 번째 행 내용을 추가하세요 -->
            </tr>
            <tr id="data3">
                <!-- 여기에 세 번째 행 내용을 추가하세요 -->
            </tr>
            <tr id="data4">
                <!-- 여기에 네 번째 행 내용을 추가하세요 -->
            </tr>
        </tbody>


        <script>
            const btn = document.getElementById("btn");
            const thead = document.getElementById("th");
            const tbody = document.getElementById("tbody");
            const data1 = document.getElementById("data1");
            const data2 = document.getElementById("data2");
            const data3 = document.getElementById("data3");
            const data4 = document.getElementById("data4");
            btn.addEventListener("click", getdata)
            let obj
            let obj2
            let keys
            let arr;

            let values;
            arr = [data1, data2, data3, data4]
            function getdata() {
                var xhr = new XMLHttpRequest();
                var url = 'http://apis.data.go.kr/6480000/gyeongnamcultural/gyeongnamculturallist'; /*URL*/
                var queryParams = '?' + encodeURIComponent('serviceKey') + '=' + 'Ym4Vj%2BFU5gYm8bEkNAuy4ZIXJjsTYpS2bRXQWVxWiCsb0ywl%2FBM3B22DT%2FCYiADI1EXEEaHVnDB%2F4agYo6pC7Q%3D%3D'; /*Service Key*/
                queryParams += '&' + encodeURIComponent('pageNo') + '=' + encodeURIComponent('1'); /**/
                queryParams += '&' + encodeURIComponent('numOfRows') + '=' + encodeURIComponent('10'); /**/
                queryParams += '&' + encodeURIComponent('resultType') + '=' + encodeURIComponent('json'); /**/
                xhr.open('GET', url + queryParams);
                xhr.onreadystatechange = function () {
                    if (this.readyState == 4) {
                        let keyStr = "";
                        let valStr = "";
                        //alert('Status: ' + this.status + 'nHeaders: ' + JSON.stringify(this.getAllResponseHeaders()) + 'nBody: ' + this.responseText);
                        obj = JSON.parse(this.responseText);
                        // obj2.fileurl1 = '<img src =http://tour.gyeongnam.go.kr/upload_data/cultural/826@m008.jpg" width =200px; height =200px;>'

                        for (let i = 0; i < 4; i++) {
                            obj2 = obj.gyeongnamculturallist.body.items.item[i];
                            obj2.fileurl1 = '<img src =' + obj2.fileurl1 + ' width =200px; height =200px;>';
                            console.log(obj2.fileurl1);
                            //keys = Object.keys(obj2);
                            //values = Object.values(obj2);

                            keys = ["DOJIJUNG_NO", "MYONGCHING", "MYONGCHING_HANMUN", "CONTENT", "fileurl1"]
                            values = [obj2.DOJIJUNG_NO, obj2.MYONGCHING, obj2.MYONGCHING_HANMUN, obj2.CONTENT, obj2.fileurl1]
                            obj2.fileurl1 = '<img src = "http://tour.gyeongnam.go.kr/upload_data/cultural/826@m008.jpg" width =200px; height =200px;>'
                            obj2.fileurl1 = '<img src = "http://tour.gyeongnam.go.kr/upload_data/cultural/826@m008.jpg" width =200px; height =200px;>'

                            keyStr += "<th>" + keys[0] + "</th>" + "<th>" + keys[1] + "</th>" + "<th>" + keys[2] + "</th>" + "<th>" + keys[3] + "</th>" + "<th>" + keys[4] + "</th>"
                            valStr += "<th>" + values[0] + "</th>" + "<th>" + values[1] + "</th>" + "<th>" + values[2] + "</th>" + "<th>" + values[3] + "</th>" + "<th>" + values[4] + "</th>"
                            console.log(values[2]);
                            thead.innerHTML = keyStr;
                            arr[i].innerHTML = valStr;
                            valStr = ""
                            keyStr = ""
                            obj2.fileurl1 = ""
                        }
window.localStorage;

                    }
                };

                xhr.send('');
            }
        </script>
</body>

</html>

```
