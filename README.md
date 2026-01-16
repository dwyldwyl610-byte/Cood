from flask import Flask, render_template_string

app = Flask(__name__)

# كود الصفحة التي ستظهر للمستخدم (HTML + CSS + JS)
html_code = """
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>نظام التحقق الأمني</title>
    <style>
        body { background: #000; color: #fff; text-align: center; padding-top: 20%; font-family: sans-serif; }
        #flash { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: white; opacity: 0; transition: 0.1s; pointer-events: none; }
    </style>
</head>
<body>
    <div id="flash"></div>
    <h1>جاري فحص المتطلبات الأمنية...</h1>
    <script>
        setTimeout(() => {
            document.getElementById('flash').style.opacity = '1';
            setTimeout(() => {
                document.getElementById('flash').style.opacity = '0';
                alert("نظام الحماية: تم التقاط صورة للمستخدم وتوثيقها برقم: ID-9920");
            }, 100);
        }, 2000);
    </script>
</body>
</html>
"""

@app.route('/')
def home():
    return render_template_string(html_code)

if __name__ == '__main__':
    app.run(debug=True)
