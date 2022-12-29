<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>学习强国跳转页面</title>
    <script src="qrcode.js"></script>
    <meta content=”width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0;” name=”viewport” >
    <style>
        .wx{
            font-size: 30px;
            color: red;
        }
    </style>
</head>
<body>
<div>
    <button><a id="login" href="#"><h1>点击登录跳转学习强国app</h1></a></button>
</div>
<div id="wx" class="wx"></div>
<div id="qrcode" style="margin-top: 10px">
    <img id="img" src="#"  alt="#"/>
</div>
</body>
<script>
    function load() {
        if (isWechat()){
            document.getElementById("wx").innerText = "当前为微信环境，请点击右上角浏览器中打开"
        }
        let search = window.location.search
        search = search.substring(1,search.length)
        document.getElementById("login").setAttribute("href","dtxuexi://appclient/page/study_feeds?url="+search)
        console.log(unescape(search))
        let imgBase64 = jrQrcode.getQrBase64(unescape(search), {});
        document.getElementById("img").setAttribute("src",imgBase64)
        document.getElementById("login").click()
    }
    function isWechat() {
        return /MicroMessenger/i.test(window.navigator.userAgent);
    }
    load()

</script>
</html>
