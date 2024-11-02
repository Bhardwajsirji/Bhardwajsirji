<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Questionnaire with Love Letter</title>
    <style>
        /* Global Styles */
        * {
            box-sizing: border-box;
        }
        body {
            margin: 0;
            padding: 0;
            font-family: 'Comic Sans MS', cursive, sans-serif;
            background-color: #ffebcd;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #FFDEE9 0%, #B5FFFC 100%);
            overflow: hidden;
        }

        /* Main question container */
        .question-container {
            background-color: #ff6f61;
            color: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.5);
            font-family: 'Courier New', Courier, monospace;
            border: 2px solid #fae1dd;
            animation: slideIn 0.5s forwards;
            opacity: 0; /* Start invisible */
        }

        @keyframes slideIn {
            from {
                transform: translateY(-50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        h1 {
            color: #f1faee;
            text-shadow: 2px 2px #2a9d8f;
            font-weight: bold;
            animation: fadeIn 1s ease-in; /* Fade-in effect */
        }

        p, label {
            color: #ffffff;
            font-size: 18px;
            font-weight: bold; /* Make text bold */
            animation: fadeIn 1s ease-in; /* Fade-in effect for paragraphs */
        }

        /* Date input and button styling */
        input[type="date"] {
            padding: 12px;
            margin: 15px 0;
            width: 100%;
            border-radius: 8px;
            border: 1px solid #f4a261;
            font-size: 16px;
            background-color: #fefae0;
            color: #264653;
            transition: border-color 0.3s ease; /* Smooth transition */
        }

        input[type="date"]:focus {
            border-color: #e63946; /* Change border color on focus */
            outline: none; /* Remove default outline */
        }

        button {
            background-color: #e76f51;
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            animation: bounce 1s infinite; /* Bounce animation */
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-10px);
            }
            60% {
                transform: translateY(-5px);
            }
        }

        button:hover {
            background-color: #f4a261;
            transform: scale(1.05);
        }

        /* Result section */
        #time-spent {
            display: none;
            margin-top: 20px;
            color: #1d3557;
            font-size: 24px;
            font-weight: bold;
            text-align: center;
            animation: fadeIn 0.5s forwards; /* Fade-in effect */
            opacity: 0; /* Start invisible */
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        #time-description {
            margin-top: 10px;
            color: #457b9d;
            font-size: 22px;
            font-weight: bold;
            animation: fadeIn 0.5s forwards; /* Fade-in effect */
        }

        /* Love letter container */
        #love-letter {
            display: none;
            color: #333;
            font-size: 22px;
            margin-top: 20px;
            text-align: center;
            line-height: 1.6;
        }

        /* Heart background for love letter page */
        .heart-background {
            background: radial-gradient(circle at top left, #ff6f61, #fae1dd);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            animation: heartbeat 1.5s infinite; /* Heartbeat effect */
        }

        @keyframes heartbeat {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
        }

        .love-letter {
            background-color: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            text-align: center;
            font-family: 'Dancing Script', cursive;
            font-size: 28px;
            animation: fadeIn 0.5s forwards; /* Fade-in effect for love letter */
        }

        .typing {
            overflow: hidden; /* Ensures the text is hidden before typing */
            white-space: nowrap; /* Prevents text wrap */
            border-right: .15em solid orange; /* Typing effect cursor */
            width: 0; /* Start width 0 */
            animation: typing 4s steps(40, end), blink-caret .75s step-end infinite; /* Typing animation */
            font-weight: bold; /* Make typing text bold */
            color: #e63946; /* Text color */
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: orange; }
        }
    </style>
</head>
<body>
    <div class="question-container" id="questionBox">
        <h1>Questionnaire</h1>
        <p>When did we both come into a relationship?</p>
        <input type="date" id="userAnswer">
        <button onclick="checkAnswer()">Submit</button>
        <p id="message" style="color: yellow;"></p>
    </div>

    <!-- Time spent section -->
    <div id="time-spent">
        <h1>Our Time Together</h1>
        <p id="time-description">Together, we have faced ups and downs, yet our bond has only grown stronger with every moment.</p>
        <div id="time-display"></div>
        <button id="nextButton" onclick="showLoveLetter()">Read Love Letter</button>
    </div>

    <script>
        function checkAnswer() {
            const correctAnswer = "2023-11-13";
            const userAnswer = document.getElementById('userAnswer').value;
            if (userAnswer === correctAnswer) {
                document.getElementById('message').innerHTML = "Correct! Moving forward...";
                setTimeout(() => {
                    document.getElementById('questionBox').style.display = 'none';
                    showTimeSpent();
                }, 2000);
            } else {
                document.getElementById('message').innerHTML = "Sorry, wrong answer. Try again.";
            }
        }

        function showTimeSpent() {
            document.getElementById('time-spent').style.display = 'block';
            document.getElementById('time-spent').style.opacity = '1'; // Fade in effect
            const startDate = new Date("2023-11-13").getTime();
            const endDate = new Date().getTime();
            const totalHours = Math.floor((endDate - startDate) / (1000 * 60 * 60));
            const totalDays = Math.floor((endDate - startDate) / (1000 * 60 * 60 * 24));
            const totalMonths = Math.floor(totalDays / 30);
            document.getElementById('time-display').innerHTML = `
                Together Time:<br>
                - ${totalHours} hours<br>
                - ${totalDays} days<br>
                - ${totalMonths} months
            `;
        }

        function showLoveLetter() {
            const newWindow = window.open("", "_blank");
            newWindow.document.write(`
                <!DOCTYPE html>
                <html lang="en">
                <head>
                    <meta charset="UTF-8">
                    <meta name="viewport" content="width=device-width, initial-scale=1.0">
                    <title>Love Letter</title>
                    <style>
                        body {
                            font-family: 'Dancing Script', cursive;
                            color: #e63946;
                            background: radial-gradient(circle at center, #ff6f61, #fae1dd);
                            display: flex;
                            justify-content: center;
                            align-items: center;
                            height: 100vh;
                            margin: 0;
                        }
                        .love-letter {
                            background-color: rgba(255, 255, 255, 0.95);
                            padding: 30px;
                            border-radius: 15px;
                            text-align: center;
                            max-width: 500px;
                            line-height: 1.8;
                            font-size: 24px;
                            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
                            animation: fadeIn 0.5s forwards; /* Fade-in effect for love letter */
                        }
                        .typing {
                            overflow: hidden; /* Ensures the text is hidden before typing */
                            white-space: nowrap; /* Prevents text wrap */
                            border-right: .15em solid orange; /* Typing effect cursor */
                            width: 0; /* Start width 0 */
                            animation: typing 4s steps(40, end), blink-caret .75s step-end infinite; /* Typing animation */
                            font-weight: bold; /* Make typing text bold */
                            color: #e63946; /* Text color */
                        }

                        @keyframes typing {
                            from { width: 0; }
                            to { width: 100%; }
                        }

                        @keyframes blink-caret {
                            from, to { border-color: transparent; }
                            50% { border-color: orange; }
                        }
                    </style>
                </head>
                <body>
                    <div class="love-letter">
                        <div class="typing">My Sweetheart,</div>
                        <p> Aap mere liye bhout hi jyada kimti ho .</p>
                        <p> hume jese ye saal ii sath reh kr nikla vese hi muje aapke sath hr saal jena hai</p>
                        <p> bda jyada pyar krta hun meh aapse </p>
                        <p> I love you supriyaaa</p>
                    </div>
                </body>
                </html>
            `);
            newWindow.document.close();
        }
    </script>
</body>
</html>