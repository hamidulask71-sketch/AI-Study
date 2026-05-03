# 🎓 AI Study - তোমার AI লার্নিং অ্যাসিস্ট্যান্ট

![Student Friendly](https://img.shields.io/badge/For-Students-brightgreen)
![HTML](https://img.shields.io/badge/HTML-5-orange)
![Made with Love](https://img.shields.io/badge/Made%20with-❤️-red)

**AI Study** হলো একটি সহজ ও স্মার্ট ওয়েব অ্যাপ্লিকেশন যা স্টুডেন্টদের পড়াশোনায় সাহায্য করার জন্য তৈরি করা হয়েছে।

## ✨ কেন এই অ্যাপটি ব্যবহার করবেন?

- সহজ ইন্টারফেস — কোনো জটিলতা নেই
- যেকোনো বিষয়ে দ্রুত শেখার সুযোগ
- মোবাইল ও কম্পিউটার উভয়েই চলবে
- বিনামূল্যে এবং ওপেন সোর্স

## 🚀 মেইন ফিচারসমূহ (স্টুডেন্টদের জন্য)

- 📚 **স্টাডি ম্যাটেরিয়াল** সংরক্ষণ ও ব্যবস্থাপনা
- 💡 **AI চ্যাট** (প্রশ্ন করুন, উত্তর পান)
- 📝 **নোটস** তৈরি ও সংরক্ষণ করুন
- 🎯 **কুইজ ও প্র্যাকটিস** মোড (ভবিষ্যতে)
- 🌙 **ডার্ক মোড** — রাতে পড়ার জন্য সুবিধাজনক

## 🛠️ ব্যবহৃত প্রযুক্তি

- HTML5
- CSS3
- JavaScript
- XML (রিসোর্সের জন্য)

## 📥 কীভাবে ব্যবহার করবেন (খুব সহজ)

1. এই রিপোজিটরিটি ডাউনলোড করুন অথবা ক্লোন করুন:
   ```bash
   git clone https://github.com/hamidulask71-sketch/AI-Study.git
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>আমার চ্যাটবোর্ড</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .chat-container {
            width: 400px;
            max-width: 90%;
            height: 600px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        .chat-header {
            background: #4a5568;
            color: white;
            padding: 20px;
            text-align: center;
            font-size: 1.5rem;
            font-weight: bold;
        }

        .chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .message {
            max-width: 80%;
            padding: 10px 15px;
            border-radius: 15px;
            word-wrap: break-word;
        }

        .user-message {
            background: #667eea;
            color: white;
            align-self: flex-end;
            border-bottom-right-radius: 5px;
        }

        .bot-message {
            background: #e2e8f0;
            color: #2d3748;
            align-self: flex-start;
            border-bottom-left-radius: 5px;
        }

        .chat-input-area {
            display: flex;
            padding: 20px;
            background: #f7fafc;
            gap: 10px;
            border-top: 1px solid #e2e8f0;
        }

        #userInput {
            flex: 1;
            padding: 10px;
            border: 1px solid #cbd5e0;
            border-radius: 25px;
            outline: none;
            font-size: 1rem;
        }

        #sendBtn {
            background: #667eea;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            transition: transform 0.2s;
        }

        #sendBtn:hover {
            transform: scale(1.05);
            background: #5a67d8;
        }

        /* স্ক্রলবার স্টাইল */
        .chat-messages::-webkit-scrollbar {
            width: 8px;
        }
        .chat-messages::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        .chat-messages::-webkit-scrollbar-thumb {
            background: #cbd5e0;
            border-radius: 4px;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-header">
            🤖 আমার চ্যাটবোর্ড
        </div>
        <div class="chat-messages" id="chatMessages">
            <div class="message bot-message">
                হ্যালো! আমি আপনার সাহায্যকারী বট। আপনি যা জিজ্ঞাসা করবেন, যথাসাধ্য উত্তর দেব। 🤝
            </div>
        </div>
        <div class="chat-input-area">
            <input type="text" id="userInput" placeholder="এখানে লিখুন...">
            <button id="sendBtn">পাঠান</button>
        </div>
    </div>

    <script>
        const chatMessages = document.getElementById('chatMessages');
        const userInput = document.getElementById('userInput');
        const sendBtn = document.getElementById('sendBtn');

        // সহজ উত্তর দেওয়ার ফাংশন (আপনি চাইলে API বা বড় মডেল যোগ করতে পারেন)
        function getBotReply(userText) {
            userText = userText.toLowerCase().trim();

            // কিছু সাধারণ প্রশ্নের উত্তর (টেমপ্লেট)
            if (userText.includes('নাম') || userText.includes('কে তুমি')) {
                return 'আমি আপনার সহচর AI বট। আমার নাম চ্যাটবোর্ড বট!';
            } 
            else if (userText.includes('কেমন আছ') || userText.includes('কেমন আছো')) {
                return 'আমি খুব ভালো আছি, ধন্যবাদ! আপনি কেমন আছেন?';
            }
            else if (userText.includes('ধন্যবাদ')) {
                return 'আপনাকে ধন্যবাদ! আপনার কোন প্রশ্ন থাকলে জিজ্ঞাসা করুন।';
            }
            else if (userText.includes('হ্যালো') || userText.includes('হাই') || userText.includes('ওহে')) {
                return 'হ্যালো! কি সাহায্য করতে পারি?';
            }
            else if (userText.includes('সময়')) {
                const now = new Date();
                return `বর্তমান সময়: ${now.toLocaleTimeString('bn-BD')}`;
            }
            else if (userText.includes('ওপেন এআই') || userText.includes('chatgpt')) {
                return 'আমি একটি কাস্টম চ্যাটবট। আপনি চাইলে API ব্যবহার করে ChatGPT ইন্টিগ্রেট করতে পারেন।';
            }
            else if (userText.includes('বিদায়') || userText.includes('বাই')) {
                return 'বিদায়! ভালো থাকবেন। আবার কথা হবে। 👋';
            }
            else {
                return 'দুঃখিত, আমি এখনো এই প্রশ্নের উত্তর শিখিনি। তবে চেষ্টা করছি। আপনি অন্য কিছু জিজ্ঞাসা করতে পারেন।';
            }
        }

        function addMessage(text, sender) {
            const messageDiv = document.createElement('div');
            messageDiv.classList.add('message');
            messageDiv.classList.add(sender === 'user' ? 'user-message' : 'bot-message');
            messageDiv.innerText = text;
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        function sendMessage() {
            const userText = userInput.value.trim();
            if (userText === '') return;

            addMessage(userText, 'user');
            userInput.value = '';

            // বটের উত্তর আসতে একটু দেরি করে (রিয়ালিস্টিক ফিল)
            setTimeout(() => {
                const reply = getBotReply(userText);
                addMessage(reply, 'bot');
            }, 500);
        }

        sendBtn.addEventListener('click', sendMessage);
        userInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });
    </script>
</body>
</html>
