# 🐧 Penguin's Offensive Security — HTB CTF Writeup

## Challenge Name: Flag Command  
**Platform:** Hack The Box  
**Category:** Web  
**Difficulty:** Very Easy  
**Exploit Type:** Sensitive Information Disclosure via Unprotected API Endpoint

---

### 📖 Description

Greetings and welcome to the world of **Penguin's Offensive Security**!

This repository contains the write-up for the Hack The Box CTF challenge titled **Flag Command**. This is a beginner-level, web-based challenge. In the future, we will explore more complex and intriguing scenarios.

---

### 🛠️ Steps to Solve

1. **Start the Instance**  
   Launch the challenge machine from Hack The Box.

   ![Start Instance](/imgs/1.png)

2. **Explore the Web Interface**  
   Navigate to the webpage provided by the instance.

   ![Web Page](/imgs/2.png)

3. **Play Around**  
   Enter the `help` command and explore the CLI-based interface.

   ![Help Command](/imgs/3.png)

4. **Intercept HTTP Requests**  
   Open Burp Suite and go to:
```
Proxy > HTTP History
```

This will show all the paths visited during page load.

![HTTP History](/imgs/4.png)

You will find several endpoints:

```
/
/static/terminal/js/main.js
/static/terminal/js/game.js
/static/terminal/js/command.js
/api/options
/favicon.ico (404)
```

5. **Investigate `/api/options` Endpoint**  
This endpoint looks interesting — visit it directly.

![API Response](/imgs/5.png)

You'll see a list of options, including **hidden commands** that were not shown in the game interface.

6. **Use the Hidden Option**  
Copy the hidden/secret command from the API response and input it into the game's CLI.

![Flag Found](/imgs/6.png)

**Boom! 🎉 Flag Retrieved.**

---

### 🧠 Vulnerability Identified

**Sensitive Information Disclosure** via the unprotected `/api/options` endpoint.  
This endpoint revealed internal game logic, including secret commands and options not visible to users on the frontend, allowing unauthorized access to the final flag.

---

### 📌 Conclusion

This was a simple, yet valuable challenge to understand how insecure API endpoints can lead to unintended disclosure of sensitive information. Always monitor and secure your backend routes!

---

### 🔐 Try It Yourself

Now it's your turn! Head over to [Hack The Box](https://hackthebox.com) and give **Flag Command** a shot.

---

**Author:** Reza Balouch  
**PengOffSec | Penguin's Offensive Security**
