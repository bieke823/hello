<!DOCTYPE html>
<html>
<head>
    <title>基于LLM大语言模型面向学生学习编程网站</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        header {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px;
        }

        nav {
            background-color: #eee;
            padding: 10px;
            display: flex;
            justify-content: center;
        }

        nav a {
            color: #333;
            text-decoration: none;
            margin: 0 10px;
            font-weight: bold;
        }

        main {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        section {
            margin-bottom: 20px;
            border: 1px solid #ccc;
            padding: 20px;
            background-color: #fff;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        h1 {
            margin: 0;
        }

        footer {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px;
        }

        #login-section {
            text-align: center;
        }

        #login-form {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        #login-form label {
            margin-bottom: 10px;
        }

        #login-form input[type="text"],
        #login-form input[type="password"] {
            width: 200px;
            padding: 5px;
            margin-bottom: 10px;
        }

        #login-form button[type="submit"] {
            padding: 10px 20px;
            background-color: #333;
            color: #fff;
            border: none;
            cursor: pointer;
        }

        #forum-messages {
            max-height: 200px;
            overflow-y: auto;
            border: 1px solid #ccc;
            padding: 10px;
            margin-bottom: 10px;
        }

        #forum-input {
            margin-bottom: 10px;
        }

        #forum-send-btn {
            background-color: #333;
            color: #fff;
            padding: 5px 10px;
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header>
        <h1>基于LLM大语言模型面向学生学习编程网站</h1>
    </header>

    <nav>
        <a href="#" id="code-btn">编写代码</a>
        <a href="#" id="ai-btn">AI分析优化代码</a>
        <a href="#" id="forum-btn">交流论坛</a>
        <a href="#" id="login-btn">登录</a>
    </nav>

    <main>
        <section id="login-section">
            <h2>登录</h2>
            <form id="login-form">
                <label for="username">用户名:</label>
                <input type="text" id="username" name="username" required>
                <label for="password">密码:</label>
                <input type="password" id="password" name="password" required>
                <button type="submit">登录</button>
                </form>
                </section>    <section id="code-section" style="display: none;">
                    <h2>编写代码</h2>
                    <p>在这里输入你的代码：</p>
                    <textarea id="code-input" rows="10" cols="80"></textarea>
                </section>
            
                <section id="ai-section" style="display: none;">
                    <h2>AI分析优化代码</h2>
                    <p>点击下方按钮，让AI对你的代码进行分析和优化：</p>
                    <button id="analyze-btn">分析代码</button>
                    <div id="analysis-result"></div>
                </section>
            
                <section id="forum-section" style="display: none;">
                    <h2>交流论坛</h2>
                    <p>在这里和其他编程爱好者交流：</p>
                    <div id="forum-messages"></div>
                    <textarea id="forum-input" rows="5" cols="50"></textarea>
                    <button id="forum-send-btn">发送</button>
                </section>
            </main>
            
            <footer>
                版权所有 &copy; 2023 19-CodeMentorX gaoxiao03
            </footer>
            
            <script>
                // 获取登录表单元素和主页面各部分的元素
                const loginForm = document.getElementById('login-form');
                const loginSection = document.getElementById('login-section');
                const codeSection = document.getElementById('code-section');
                const aiSection = document.getElementById('ai-section');
                const forumSection = document.getElementById('forum-section');
            
                // 监听登录表单的提交事件
                loginForm.addEventListener('submit', (e) => {
                    e.preventDefault(); // 阻止表单的默认提交行为
            
                    // 获取输入的用户名和密码
                    const username = document.getElementById('username').value.trim();
                    const password = document.getElementById('password').value.trim();
            
                    // 简单验证用户名和密码是否为空
                    if (username && password) {
                        // 登录成功，执行跳转到主页面的逻辑
                        loginSection.style.display = 'none';
                        codeSection.style.display = 'block';
                        aiSection.style.display = 'block';
                        forumSection.style.display = 'block';
                    } else {
                        // 登录失败，弹出提示框
                        alert('请输入有效的用户名和密码');
                    }
                });
            </script>
            <script>
                /* 上述代码不变 */
            
                analyzeBtn.addEventListener('click', async () => {
                    const code = document.getElementById('code-input').value.trim();
                    if (code) {
                        const optimizedCode = await analyzeAndOptimizeCode(code);
                        document.getElementById('analysis-result').innerText = optimizedCode;
                    } else {
                        document.getElementById('analysis-result').innerText = '请输入代码';
                    }
                });
            
                async function analyzeAndOptimizeCode(code) {
                    try {
                        const response = await fetch('/analyze', {
                            method: 'POST',
                            headers: {
                                'Content-Type': 'application/json'
                            },
                            body: JSON.stringify({ code })
                        });
                        const data = await response.json();
                        if (response.ok) {
                            return data.optimizedCode;
                        } else {
                            throw new Error(data.error);
}
} catch (error) {
console.error(error);
return '代码优化失败';
}
}
</script>
<script>
// 用于保存论坛消息
let forumMessages = [];    // 模拟一些初始消息
    forumMessages.push({
        username: 'User1',
        message: '欢迎来到论坛！'
    });
    forumMessages.push({
        username: 'User2',
        message: '大家好！'
    });

    // 在页面加载时显示初始消息
    window.addEventListener('load', () => {
        displayForumMessages();
    });

    // 显示论坛消息
    function displayForumMessages() {
        const forumMessagesContainer = document.getElementById('forum-messages');
        forumMessages.forEach((message) => {
            const messageElement = document.createElement('p');
            messageElement.textContent = `${message.username}: ${message.message}`;
            forumMessagesContainer.appendChild(messageElement);
        });
    }

    // 发送按钮点击事件处理函数
    const forumSendBtn = document.getElementById('forum-send-btn');
    forumSendBtn.addEventListener('click', () => {
        const message = document.getElementById('forum-input').value.trim();
        if (message) {
            // 创建新的消息对象
            const newMessage = {
                username: '我', // 这里可以替换为当前登录用户的用户名
                message: message
            };

            // 将消息加入论坛消息数组
            forumMessages.push(newMessage);

            // 清空输入框
            document.getElementById('forum-input').value = '';

            // 清空论坛消息区域并重新显示所有消息
            clearForumMessages();
            displayForumMessages();
        } else {
            alert('请输入消息');
        }
    });

    // 清空论坛消息区域
    function clearForumMessages() {
        const forumMessagesContainer = document.getElementById('forum-messages');
        while (forumMessagesContainer.firstChild) {
            forumMessagesContainer.removeChild(forumMessagesContainer.firstChild);
        }
    }
</script>
</body>
</html>
            