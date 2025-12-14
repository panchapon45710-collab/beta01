from flask import Flask, render_template, request

app = Flask(__name__)

@app.route("/", methods=["GET", "POST"])
def login():
    error = ""
    if request.method == "POST":
        username = request.form["username"]
        password = request.form["password"]

        # ตัวอย่างตรวจสอบข้อมูล
        if username == "admin" and password == "1234":
            return "<h1>เข้าสู่ระบบสำเร็จ</h1>"
        else:
            error = "ชื่อผู้ใช้หรือรหัสผ่านไม่ถูกต้อง"

    return render_template("login.html", error=error)

if __name__ == "__main__":
    app.run(debug=True)
