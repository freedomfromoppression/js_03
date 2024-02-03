# js_03
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>세션 스토리지</title>
</head>
<body>
    <h3>세션 스토리지</h3>
    <hr>
    item : <input type ="text" id="item">
    cnt : <input type ="text" id="cnt">
    <button onclick="fn_save">저장</button>
    <button onclick="fn_search">검색</button>
    <div id="content"></div>
    <script>
        function fn_save(){
            let item = document.getElementById("item");
            let cnt = document.getElementById("cnt");
            sessionStorage.setItem(item.value, cnt.value);
            item.value='';
            cnt.value='';
        }
        function fn_search(){
            let item = document.getElementById("item");
            let val = sessionStorage.getItem(item.value);
            let str = "";
            if(val = null){
                str +="없음..";
            }else{
                str +="key:"+item.value + "/value:" + val + "<br>";
            }
            document.getElementById("content").innerHTML +=str;
        }
    </script>
    
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>세션 스토리지</title>
</head>
<body>
    <h3>세션 스토리지</h3>
    <hr>
    item : <input type ="text" id="item">
    cnt : <input type ="text" id="cnt">
    <button onclick="fn_save">저장</button>
    <button onclick="fn_search">검색</button>
    <div id="content"></div>
    <script>
        function fn_save(){
            let item = document.getElementById("item");
            let cnt = document.getElementById("cnt");
            localStorage.setItem(item.value, cnt.value);
            item.value='';
            cnt.value='';
        }
        function fn_search(){
            let item = document.getElementById("item");
            let val = localStorage.getItem(item.value);
            let str = "";
            if(val = null){
                str +="없음..";
            }else{
                str +="key:"+item.value + "/value:" + val + "<br>";
            }
            document.getElementById("content").innerHTML +=str;
        }
    </script>
    
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>쿠키</title>
    <script>
        function setCookie(name, val, expireDate){
            let cookieStr= name+ "=" + escape(val) +
            ((expireDate == null)? "" : 
            ("; expires=" +expireDate.toUTCString()));
            document.cookie = cookieStr;
        }4
        function getCookie(name){
            let str = name + "=";
            // 쿠키는 속성별 구분을 ; 으로 함.
            let pairs = document.cookie.split(';');
            for(let i=0 ; i<pairs.length; i++){
                let pair = pairs[i].trim(); //공백제거
                // key=value
                let unit = pair.split("=");
                if(unit[0] == name){
                    return unescape(unit[1]);
                }
            }
        }
        let userName = getCookie("username");
        let count = getCookie("count");
        let expires = new Date();
        //쿠키에 username이라는 속성
        if(userName == null){
            count=0
            while(true){
                userName = prompt("이름을 입력하세요.");
                if(userName == null || userName == ''){
                    alert("이름을 입력하셔야 입장가능..");
                }else{
                       //유효기간 1년 쿠키
                       expires.setTime(expires.getTime() + (365 * 24 * 60 * 80 * 1000));
                       setCookie("username", userName, expires);
                       break;
                }
            }
        }
        count ++;
        expires.setTime(expires.getTime() + (365 * 24 * 60 * 60 * 1000));
        setCookie('count', count, expires);
        document.write("<p> 어서오세요" 
            + userName + "님의" + count + "번째 방문을 환영합니다.</p>");
    </script>
</head>
<body>
    <h3>인코딩과 디코딩</h3>
    <!--
        인코딩은 문자를 컴퓨터에게 저장하거나 통신에 사용할 목적으로 부화하는 방법
        javascript 인코딩 디코딩 함수
        1.escape() 영문, 숫자, 일부(@,*,+...) 특수문자를 제외하고 인코딩함
        | unescape()
        2.encodeURL() 인터넷 주소에 사용되는 일부 특수문자(: ; / = , ? &)제외하고 인코딩
          decodeURL()
        3.encodeUTLComponent() 알파벳과 숫자를 제외한 모든 문자를 인코딩(UTF-8과 같음)
        3.encodeUTLComponent()
    -->
    <script>
        let url= "https://search.naver.com/search.naver?query=미래융합교육원";
        let es= escape(url);
        let enco= encodeUTL(url);
        let encoC= encodeURLIComponent(url);
        console.log('1.escape:');
        console.log('encodeURl:');
        console.log('encodeURIComponent:',encoC);
        console.log('unescape:',unescape(es));
        console.log('decodeURL:',decodeURL(es));
        console.log('escape:'es);
        
    </script>

    
</body>
</html>
