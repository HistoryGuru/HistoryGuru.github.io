layout: page
title: "PAGE-TITLE"
permalink: /AsteroidGame
<!doctype html>

<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Chinese Word Defense</title>

<style>

@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&display=swap');


* {

margin: 0;

padding: 0;

box-sizing: border-box;

}


body {

font-family: 'Orbitron', monospace;

background: linear-gradient(135deg, #0c0c2e 0%, #1a1a4a 50%, #2d1b69 100%);

color: white;

overflow: hidden;

height: 100vh;

box-sizing: border-box;

}


.game-container {

position: relative;

width: 100vw;

height: 100vh;

overflow: hidden;

}


.stars {

position: absolute;

width: 100%;

height: 100%;

background-image:

radial-gradient(2px 2px at 20px 30px, #eee, transparent),

radial-gradient(2px 2px at 40px 70px, rgba(255,255,255,0.8), transparent),

radial-gradient(1px 1px at 90px 40px, #fff, transparent),

radial-gradient(1px 1px at 130px 80px, rgba(255,255,255,0.6), transparent),

radial-gradient(2px 2px at 160px 30px, #fff, transparent);

background-repeat: repeat;

background-size: 200px 100px;

animation: twinkle 3s ease-in-out infinite alternate;

}


@keyframes twinkle {

0% { opacity: 0.8; }

100% { opacity: 1; }

}


.earth {

position: absolute;

bottom: -100px;

left: 50%;

transform: translateX(-50%);

width: 300px;

height: 300px;

background: radial-gradient(circle at 30% 30%, #4a90e2, #2171b5, #1e3a8a);

border-radius: 50%;

box-shadow:

0 0 50px rgba(74, 144, 226, 0.5),

inset -20px -20px 50px rgba(0, 0, 0, 0.3);

}


.earth::before {

content: '';

position: absolute;

top: 20%;

left: 10%;

width: 40%;

height: 30%;

background: #22c55e;

border-radius: 50% 30% 60% 40%;

opacity: 0.8;

}


.earth::after {

content: '';

position: absolute;

top: 50%;

right: 20%;

width: 30%;

height: 25%;

background: #22c55e;

border-radius: 40% 60% 30% 50%;

opacity: 0.8;

}


.asteroid {

position: absolute;

width: 80px;

height: 80px;

background: linear-gradient(135deg, #8b5a3c, #654321, #4a2c17);

border-radius: 50% 40% 60% 30%;

display: flex;

align-items: center;

justify-content: center;

font-size: 24px;

font-weight: bold;

color: #fff;

text-shadow: 2px 2px 4px rgba(0,0,0,0.8);

box-shadow:

0 0 20px rgba(139, 90, 60, 0.6),

inset -10px -10px 20px rgba(0, 0, 0, 0.4);

animation: rotate 3s linear infinite;

}


@keyframes rotate {

0% { transform: rotate(0deg); }

100% { transform: rotate(360deg); }

}


.asteroid.exploding {

animation: explode 0.5s ease-out forwards;

}


@keyframes explode {

0% {

transform: scale(1);

opacity: 1;

}

50% {

transform: scale(1.5);

background: radial-gradient(circle, #ff6b35, #f7931e, #ffcc02);

}

100% {

transform: scale(2);

opacity: 0;

}

}


.laser-beam {

position: absolute;

width: 4px;

background: linear-gradient(to top, #00ff00, #ffffff, #00ff00);

box-shadow:

0 0 10px #00ff00,

0 0 20px #00ff00,

0 0 30px #00ff00;

z-index: 50;

opacity: 0;

animation: laser-fire 0.3s ease-out forwards;

}


@keyframes laser-fire {

0% {

opacity: 1;

transform: scaleY(0);

transform-origin: bottom;

}

50% {

opacity: 1;

transform: scaleY(1);

}

100% {

opacity: 0;

transform: scaleY(1);

}

}


.ui {

position: absolute;

top: 20px;

left: 20px;

z-index: 100;

}


.score {

font-size: 24px;

font-weight: 700;

margin-bottom: 10px;

text-shadow: 2px 2px 4px rgba(0,0,0,0.8);

}


.lives {

font-size: 20px;

color: #ef4444;

font-weight: 700;

text-shadow: 2px 2px 4px rgba(0,0,0,0.8);

}


.input-area {

position: absolute;

bottom: 100px;

left: 50%;

transform: translateX(-50%);

text-align: center;

z-index: 100;

}


.word-input {

padding: 15px 25px;

font-size: 24px;

font-family: 'Orbitron', monospace;

background: rgba(0, 0, 0, 0.8);

border: 3px solid #4a90e2;

border-radius: 10px;

color: white;

text-align: center;

width: 300px;

margin-bottom: 15px;

outline: none;

transition: all 0.3s ease;

}


.word-input:focus {

border-color: #22c55e;

box-shadow: 0 0 20px rgba(34, 197, 94, 0.5);

}


.translation {

font-size: 18px;

color: #94a3b8;

margin-bottom: 10px;

min-height: 25px;

}


.game-over {

position: absolute;

top: 50%;

left: 50%;

transform: translate(-50%, -50%);

text-align: center;

background: rgba(0, 0, 0, 0.9);

padding: 40px;

border-radius: 20px;

border: 3px solid #ef4444;

display: none;

z-index: 200;

}


.game-over h2 {

font-size: 36px;

color: #ef4444;

margin-bottom: 20px;

}


.restart-btn {

padding: 15px 30px;

font-size: 20px;

font-family: 'Orbitron', monospace;

background: linear-gradient(135deg, #4a90e2, #2171b5);

border: none;

border-radius: 10px;

color: white;

cursor: pointer;

transition: all 0.3s ease;

margin-top: 20px;

}


.restart-btn:hover {

background: linear-gradient(135deg, #2171b5, #1e3a8a);

transform: translateY(-2px);

}


.instructions {

position: absolute;

top: 20px;

right: 20px;

background: rgba(0, 0, 0, 0.7);

padding: 15px;

border-radius: 10px;

font-size: 14px;

max-width: 250px;

}


.menu-screen {

position: absolute;

top: 0;

left: 0;

width: 100%;

height: 100%;

background: rgba(0, 0, 0, 0.9);

display: flex;

flex-direction: column;

align-items: center;

justify-content: center;

z-index: 300;

overflow: hidden;

}


.floating-space-object {

position: absolute;

opacity: 0.8;

animation: float-across 15s linear infinite;

z-index: 301;

color: white;

font-size: 20px;

}


.space-star {

animation: float-across 20s linear infinite, twinkle-star 2s ease-in-out infinite alternate;

}


.space-star-small {

font-size: 15px;

animation: float-across 25s linear infinite, twinkle-star 3s ease-in-out infinite alternate;

}


.space-star-large {

font-size: 25px;

animation: float-across 18s linear infinite, twinkle-star 1.5s ease-in-out infinite alternate;

}


@keyframes twinkle-star {

0% { opacity: 0.4; }

100% { opacity: 1; }

}


@keyframes float-across {

0% {

transform: translateX(-100px) translateY(0px);

opacity: 0;

}

10% {

opacity: 0.6;

}

90% {

opacity: 0.6;

}

100% {

transform: translateX(calc(100vw + 100px)) translateY(-50px);

opacity: 0;

}

}


.menu-title {

font-size: 48px;

font-weight: 900;

color: #4a90e2;

text-shadow: 0 0 20px rgba(74, 144, 226, 0.8);

margin-bottom: 20px;

text-align: center;

}


.menu-subtitle {

font-size: 20px;

color: #94a3b8;

margin-bottom: 50px;

text-align: center;

}


.difficulty-buttons {

display: flex;

flex-direction: column;

gap: 20px;

align-items: center;

}


.difficulty-btn {

padding: 20px 40px;

font-size: 24px;

font-family: 'Orbitron', monospace;

font-weight: 700;

border: 3px solid;

border-radius: 15px;

color: white;

cursor: pointer;

transition: all 0.3s ease;

background: rgba(0, 0, 0, 0.5);

min-width: 200px;

text-align: center;

}


.difficulty-btn.easy {

border-color: #22c55e;

box-shadow: 0 0 20px rgba(34, 197, 94, 0.3);

}


.difficulty-btn.easy:hover {

background: rgba(34, 197, 94, 0.2);

box-shadow: 0 0 30px rgba(34, 197, 94, 0.6);

transform: translateY(-3px);

}


.difficulty-btn.medium {

border-color: #f59e0b;

box-shadow: 0 0 20px rgba(245, 158, 11, 0.3);

}


.difficulty-btn.medium:hover {

background: rgba(245, 158, 11, 0.2);

box-shadow: 0 0 30px rgba(245, 158, 11, 0.6);

transform: translateY(-3px);

}


.difficulty-btn.hard {

border-color: #ef4444;

box-shadow: 0 0 20px rgba(239, 68, 68, 0.3);

}


.difficulty-btn.hard:hover {

background: rgba(239, 68, 68, 0.2);

box-shadow: 0 0 30px rgba(239, 68, 68, 0.6);

transform: translateY(-3px);

}


.difficulty-description {

font-size: 14px;

color: #64748b;

margin-top: 5px;

}


.back-button {

position: absolute;

top: 30px;

left: 30px;

padding: 12px 20px;

font-size: 16px;

font-family: 'Orbitron', monospace;

background: linear-gradient(135deg, #64748b, #475569);

border: 2px solid #94a3b8;

border-radius: 10px;

color: white;

cursor: pointer;

transition: all 0.3s ease;

}


.back-button:hover {

background: linear-gradient(135deg, #475569, #334155);

transform: translateY(-2px);

}

</style>

<style>@view-transition { navigation: auto; }</style>

<script src="/_sdk/data_sdk.js" type="text/javascript"></script>

<script src="/_sdk/element_sdk.js" type="text/javascript"></script>

<script src="https://cdn.tailwindcss.com" type="text/javascript"></script>

</head>

<body>

<div class="game-container">

<div class="stars"></div>

<div class="earth"></div>

<div class="menu-screen" id="teacherModeScreen"><!-- Floating space objects -->

<div class="floating-space-object space-star" style="top: 15%; animation-delay: 0s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 25%; animation-delay: 2s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 35%; animation-delay: 4s;">

★

</div>

<div class="floating-space-object space-star" style="top: 45%; animation-delay: 6s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 55%; animation-delay: 8s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 65%; animation-delay: 10s;">

★

</div>

<div class="floating-space-object space-star" style="top: 75%; animation-delay: 12s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 85%; animation-delay: 14s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 10%; animation-delay: 16s;">

★

</div>

<div class="floating-space-object space-star" style="top: 90%; animation-delay: 18s;">

✦

</div>

<h1 class="menu-title">Chinese Word Defense</h1>

<p class="menu-subtitle">Select Your Mode</p>

<div class="difficulty-buttons">

<div class="difficulty-btn easy" onclick="selectStudentMode()">

STUDENT MODE

<div class="difficulty-description">

Enter a link or use default vocabulary

</div>

</div>

<div class="difficulty-btn medium" onclick="selectTeacherMode()">

TEACHER MODE

<div class="difficulty-description">

Create custom vocabulary and get link

</div>

</div>

</div>

</div>

<div class="menu-screen" id="customVocabScreen" style="display: none;"><!-- Floating space objects -->

<div class="floating-space-object space-star" style="top: 15%; animation-delay: 0s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 25%; animation-delay: 2s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 35%; animation-delay: 4s;">

★

</div>

<div class="floating-space-object space-star" style="top: 45%; animation-delay: 6s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 55%; animation-delay: 8s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 65%; animation-delay: 10s;">

★

</div>

<div class="floating-space-object space-star" style="top: 75%; animation-delay: 12s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 85%; animation-delay: 14s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 10%; animation-delay: 16s;">

★

</div>

<div class="floating-space-object space-star" style="top: 90%; animation-delay: 18s;">

✦

</div><button class="back-button" onclick="backToModeSelection()">← Back</button>

<h1 class="menu-title">Custom Vocabulary</h1>

<p class="menu-subtitle">Enter vocabulary in format: chinese,pinyin,english</p>

<p class="menu-subtitle" style="font-size: 14px; margin-top: -30px; margin-bottom: 30px;">Example: 你好,ni hao,hello</p><textarea id="customVocabInput" placeholder="Enter one word per line:

你好,ni hao,hello

再见,zai jian,goodbye

谢谢,xie xie,thank you" style="width: 600px; height: 300px; padding: 20px; font-size: 16px; font-family: 'Orbitron', monospace; background: rgba(0, 0, 0, 0.8); border: 3px solid #4a90e2; border-radius: 10px; color: white; resize: vertical; margin-bottom: 20px;"></textarea>

<div style="display: flex; gap: 20px; justify-content: center;"><button class="difficulty-btn medium" onclick="confirmCustomVocab()" style="min-width: 200px;"> GENERATE LINK </button>

</div>

</div>

<div class="menu-screen" id="studentLinkScreen" style="display: none;"><!-- Floating space objects -->

<div class="floating-space-object space-star" style="top: 15%; animation-delay: 0s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 25%; animation-delay: 2s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 35%; animation-delay: 4s;">

★

</div>

<div class="floating-space-object space-star" style="top: 45%; animation-delay: 6s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 55%; animation-delay: 8s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 65%; animation-delay: 10s;">

★

</div>

<div class="floating-space-object space-star" style="top: 75%; animation-delay: 12s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 85%; animation-delay: 14s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 10%; animation-delay: 16s;">

★

</div>

<div class="floating-space-object space-star" style="top: 90%; animation-delay: 18s;">

✦

</div><button class="back-button" onclick="backToModeSelection()">← Back</button>

<h1 class="menu-title">Student Mode</h1>

<p class="menu-subtitle">Enter your teacher's link or use default vocabulary</p><input type="text" id="studentLinkInput" placeholder="Paste link here (optional)" style="width: 600px; padding: 20px; font-size: 18px; font-family: 'Orbitron', monospace; background: rgba(0, 0, 0, 0.8); border: 3px solid #4a90e2; border-radius: 10px; color: white; text-align: center; margin-bottom: 30px;">

<div style="display: flex; gap: 20px; justify-content: center; flex-direction: column; align-items: center;"><button class="difficulty-btn easy" onclick="useStudentLink()" style="min-width: 300px;"> USE LINK </button> <button class="difficulty-btn medium" onclick="useDefaultVocab()" style="min-width: 300px;"> USE DEFAULT VOCABULARY </button>

</div>

</div>

<div class="menu-screen" id="linkDisplayScreen" style="display: none;"><!-- Floating space objects -->

<div class="floating-space-object space-star" style="top: 15%; animation-delay: 0s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 25%; animation-delay: 2s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 35%; animation-delay: 4s;">

★

</div>

<div class="floating-space-object space-star" style="top: 45%; animation-delay: 6s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 55%; animation-delay: 8s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 65%; animation-delay: 10s;">

★

</div>

<div class="floating-space-object space-star" style="top: 75%; animation-delay: 12s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 85%; animation-delay: 14s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 10%; animation-delay: 16s;">

★

</div>

<div class="floating-space-object space-star" style="top: 90%; animation-delay: 18s;">

✦

</div><button class="back-button" onclick="backToCustomVocab()">← Back</button>

<h1 class="menu-title">Your Vocabulary Link</h1>

<p class="menu-subtitle">Share this link with your students!</p>

<div style="background: rgba(0, 0, 0, 0.8); border: 3px solid #22c55e; border-radius: 10px; padding: 20px; margin: 20px 0; max-width: 700px; word-wrap: break-word;">

<p id="generatedLink" style="color: #22c55e; font-size: 14px; font-family: monospace; line-height: 1.6;"></p>

</div>

<div style="display: flex; gap: 20px; justify-content: center;"><button class="difficulty-btn easy" onclick="copyLink()" style="min-width: 200px;"> 📋 COPY LINK </button> <button class="difficulty-btn medium" onclick="proceedToDifficulty()" style="min-width: 200px;"> CONTINUE → </button>

</div>

</div>

<div class="menu-screen" id="menuScreen" style="display: none;"><!-- Floating space objects -->

<div class="floating-space-object space-star" style="top: 15%; animation-delay: 0s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 25%; animation-delay: 2s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 35%; animation-delay: 4s;">

★

</div>

<div class="floating-space-object space-star" style="top: 45%; animation-delay: 6s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 55%; animation-delay: 8s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 65%; animation-delay: 10s;">

★

</div>

<div class="floating-space-object space-star" style="top: 75%; animation-delay: 12s;">

✦

</div>

<div class="floating-space-object space-star-small" style="top: 85%; animation-delay: 14s;">

✧

</div>

<div class="floating-space-object space-star-large" style="top: 10%; animation-delay: 16s;">

★

</div>

<div class="floating-space-object space-star" style="top: 90%; animation-delay: 18s;">

✦

</div><button class="back-button" onclick="backToModeSelection()">← Back</button>

<h1 class="menu-title">Chinese Word Defense</h1>

<p class="menu-subtitle">Choose your difficulty</p>

<div class="difficulty-buttons">

<div class="difficulty-btn easy" onclick="startGameWithDifficulty('easy')">

EASY

<div class="difficulty-description">

Slow asteroids - Perfect for beginners

</div>

</div>

<div class="difficulty-btn medium" onclick="startGameWithDifficulty('medium')">

MEDIUM

<div class="difficulty-description">

Normal speed - Balanced challenge

</div>

</div>

<div class="difficulty-btn hard" onclick="startGameWithDifficulty('hard')">

HARD

<div class="difficulty-description">

Fast asteroids - For experts only!

</div>

</div>

</div>

</div>

<div class="ui">

<div class="score">

Score: <span id="score">0</span>

</div>

<div class="lives">

Lives: <span id="lives">3</span>

</div>

</div>

<div class="instructions"><strong>How to Play:</strong><br>

Type the pinyin for the Chinese characters shown on asteroids to destroy them before they hit Earth!

</div>

<div class="input-area">

<div class="translation" id="translation"></div><input type="text" class="word-input" id="wordInput" placeholder="Type pinyin here..." autocomplete="off">

</div>

<div class="game-over" id="gameOver">

<h2>Game Over!</h2>

<p>Final Score: <span id="finalScore">0</span></p><button class="restart-btn" onclick="restartGame()">Play Again</button>

</div>

</div>

<script>

// Default vocabulary (combined all levels from previous version)

const defaultVocabulary = [

{ chinese: '过', pinyin: 'guo', english: 'Past/Over' },

{ chinese: '去过', pinyin: 'qu guo', english: 'Have been to' },

{ chinese: '国家', pinyin: 'guo jia', english: 'Country' },

{ chinese: '英国', pinyin: 'ying guo', english: 'England/UK' },

{ chinese: '法国', pinyin: 'fa guo', english: 'France' },

{ chinese: '日本', pinyin: 'ri ben', english: 'Japan' },

{ chinese: '会', pinyin: 'hui', english: 'Can/Know how' },

{ chinese: '说', pinyin: 'shuo', english: 'Speak/Say' },

{ chinese: '语', pinyin: 'yu', english: 'Language' },

{ chinese: '英语', pinyin: 'ying yu', english: 'English language' },

{ chinese: '日语', pinyin: 'ri yu', english: 'Japanese language' },

{ chinese: '语言', pinyin: 'yu yan', english: 'Language' },

{ chinese: '汉语', pinyin: 'han yu', english: 'Chinese language' },

{ chinese: '一点儿', pinyin: 'yi dian er', english: 'A little bit' },

{ chinese: '西班牙', pinyin: 'xi ban ya', english: 'Spain' },

{ chinese: '英文', pinyin: 'ying wen', english: 'English text' },

{ chinese: '学', pinyin: 'xue', english: 'Study/Learn' },

{ chinese: '跟', pinyin: 'gen', english: 'With/Follow' },

{ chinese: '广东话', pinyin: 'guang dong hua', english: 'Cantonese' },

{ chinese: '很', pinyin: 'hen', english: 'Very' },

{ chinese: '很多', pinyin: 'hen duo', english: 'Very many' },

{ chinese: '朋友', pinyin: 'peng you', english: 'Friend' },

{ chinese: '我', pinyin: 'wo', english: 'I/Me' },

{ chinese: '有�����', pinyin: 'you de', english: 'Some' },

{ chinese: '还', pinyin: 'hai', english: 'Still/Also' },

{ chinese: '数学', pinyin: 'shu xue', english: 'Mathematics' },

{ chinese: '体育', pinyin: 'ti yu', english: 'Physical education' },

{ chinese: '美术', pinyin: 'mei shu', english: 'Art' },

{ chinese: '音乐', pinyin: 'yin yue', english: 'Music' },

{ chinese: '电脑', pinyin: 'dian nao', english: 'Computer' },

{ chinese: '科学', pinyin: 'ke xue', english: 'Science' },

{ chinese: '历史', pinyin: 'li shi', english: 'History' },

{ chinese: '地理', pinyin: 'di li', english: 'Geography' },

{ chinese: '戏剧', pinyin: 'xi ju', english: 'Drama/Theater' },

{ chinese: '谢谢', pinyin: 'xie xie', english: 'Thank you' },

{ chinese: '对不起', pinyin: 'dui bu qi', english: 'Sorry' },

{ chinese: '没关系', pinyin: 'mei guan xi', english: 'No problem' },

{ chinese: '知道', pinyin: 'zhi dao', english: 'Know' },

{ chinese: '客气', pinyin: 'ke qi', english: 'Polite' },

{ chinese: '先生', pinyin: 'xian sheng', english: 'Mister' },

{ chinese: '请问', pinyin: 'qing wen', english: 'Excuse me' },

{ chinese: '晴天', pinyin: 'qing tian', english: 'Sunny day' },

{ chinese: '小雨', pinyin: 'xiao yu', english: 'Light rain' },

{ chinese: '多云', pinyin: 'duo yun', english: 'Cloudy' },

{ chinese: '台风', pinyin: 'tai feng', english: 'Typhoon' },

{ chinese: '天气', pinyin: 'tian qi', english: 'Weather' },

{ chinese: '阴天', pinyin: 'yin tian', english: 'Overcast day' },

{ chinese: '刮风', pinyin: 'gua feng', english: 'Windy' },

{ chinese: '下雪', pinyin: 'xia xue', english: 'Snow (falling)' },

{ chinese: '春天', pinyin: 'chun tian', english: 'Spring' },

{ chinese: '冷', pinyin: 'leng', english: 'Cold' },

{ chinese: '有时候', pinyin: 'you shi hou', english: 'Sometimes' },

{ chinese: '夏天', pinyin: 'xia tian', english: 'Summer' },

{ chinese: '热', pinyin: 're', english: 'Hot' },

{ chinese: '常常', pinyin: 'chang chang', english: 'Often' },

{ chinese: '秋天', pinyin: 'qiu tian', english: 'Autumn' },

{ chinese: '冬天', pinyin: 'dong tian', english: 'Winter' },

{ chinese: '生病', pinyin: 'sheng bing', english: 'Get sick' },

{ chinese: '发烧', pinyin: 'fa shao', english: 'Have a fever' },

{ chinese: '咳嗽', pinyin: 'ke sou', english: 'Cough' },

{ chinese: '头痛', pinyin: 'tou tong', english: 'Headache' },

{ chinese: '医生', pinyin: 'yi sheng', english: 'Doctor' },

{ chinese: '舒服', pinyin: 'shu fu', english: 'Comfortable' },

{ chinese: '感冒', pinyin: 'gan mao', english: 'Cold (illness)' },

{ chinese: '休息', pinyin: 'xiu xi', english: 'Rest' },

{ chinese: '爱好', pinyin: 'ai hao', english: 'Hobby' },

{ chinese: '弹钢琴', pinyin: 'tan gang qin', english: 'Play piano' },

{ chinese: '唱歌', pinyin: 'chang ge', english: 'Sing' },

{ chinese: '听音乐', pinyin: 'ting yin yue', english: 'Listen to music' },

{ chinese: '读书', pinyin: 'du shu', english: 'Read books' },

{ chinese: '小说', pinyin: 'xiao shuo', english: 'Novel' },

{ chinese: '杂志', pinyin: 'za zhi', english: 'Magazine' },

{ chinese: '国画儿', pinyin: 'guo hua er', english: 'Chinese painting' }

];


let currentVocabulary = defaultVocabulary;


function getRandomWord() {

return currentVocabulary[Math.floor(Math.random() * currentVocabulary.length)];

}


function selectStudentMode() {

// Show student link input screen

document.getElementById('teacherModeScreen').style.display = 'none';

document.getElementById('studentLinkScreen').style.display = 'flex';

}


function selectTeacherMode() {

// Show custom vocabulary input screen

document.getElementById('teacherModeScreen').style.display = 'none';

document.getElementById('customVocabScreen').style.display = 'flex';

}


function backToModeSelection() {

document.getElementById('menuScreen').style.display = 'none';

document.getElementById('customVocabScreen').style.display = 'none';

document.getElementById('studentLinkScreen').style.display = 'none';

document.getElementById('linkDisplayScreen').style.display = 'none';

document.getElementById('teacherModeScreen').style.display = 'flex';

}


function backToCustomVocab() {

document.getElementById('linkDisplayScreen').style.display = 'none';

document.getElementById('customVocabScreen').style.display = 'flex';

}


function useDefaultVocab() {

// Use default vocabulary

currentVocabulary = defaultVocabulary;


// Show difficulty selection

document.getElementById('studentLinkScreen').style.display = 'none';

document.getElementById('menuScreen').style.display = 'flex';

}


function useStudentLink() {

const linkInput = document.getElementById('studentLinkInput').value.trim();


if (!linkInput) {

showInlineMessage('Please enter a link or use default vocabulary!', 'studentLinkInput');

return;

}


// Parse the link

if (!linkInput.startsWith('link.')) {

showInlineMessage('Invalid link format! Link should start with "link."', 'studentLinkInput');

return;

}


const vocabData = linkInput.substring(5); // Remove "link." prefix

const words = [];


try {

// Split by | to get individual words

const wordParts = vocabData.split('|');


for (let part of wordParts) {

if (!part) continue;


const fields = part.split(',');

if (fields.length >= 3) {

words.push({

chinese: fields[0],

pinyin: fields[1],

english: fields[2]

});

}

}


if (words.length === 0) {

showInlineMessage('No valid vocabulary found in link!', 'studentLinkInput');

return;

}


// Set vocabulary from link

currentVocabulary = words;


// Show difficulty selection

document.getElementById('studentLinkScreen').style.display = 'none';

document.getElementById('menuScreen').style.display = 'flex';


} catch (error) {

showInlineMessage('Error parsing link! Please check the link format.', 'studentLinkInput');

}

}


function confirmCustomVocab() {

const input = document.getElementById('customVocabInput').value.trim();


if (!input) {

showInlineMessage('Please enter at least one vocabulary word!', 'customVocabInput');

return;

}


// Parse custom vocabulary

const lines = input.split('\n');

const customWords = [];


for (let line of lines) {

line = line.trim();

if (!line) continue;


const parts = line.split(',').map(p => p.trim());

if (parts.length >= 3) {

customWords.push({

chinese: parts[0],

pinyin: parts[1],

english: parts[2]

});

}

}


if (customWords.length === 0) {

showInlineMessage('No valid vocabulary found! Please use format: chinese,pinyin,english', 'customVocabInput');

return;

}


// Set custom vocabulary

currentVocabulary = customWords;


// Generate link

const linkParts = customWords.map(word =>

`${word.chinese},${word.pinyin},${word.english}`

);

const generatedLink = 'link.' + linkParts.join('|');


// Display link

document.getElementById('generatedLink').textContent = generatedLink;

document.getElementById('customVocabScreen').style.display = 'none';

document.getElementById('linkDisplayScreen').style.display = 'flex';

}


function copyLink() {

const linkText = document.getElementById('generatedLink').textContent;


// Create temporary textarea to copy text

const tempTextarea = document.createElement('textarea');

tempTextarea.value = linkText;

tempTextarea.style.position = 'fixed';

tempTextarea.style.opacity = '0';

document.body.appendChild(tempTextarea);

tempTextarea.select();


try {

document.execCommand('copy');


// Show success message

const copyBtn = event.target;

const originalText = copyBtn.textContent;

copyBtn.textContent = '✓ COPIED!';

copyBtn.style.background = 'linear-gradient(135deg, #22c55e, #16a34a)';


setTimeout(() => {

copyBtn.textContent = originalText;

copyBtn.style.background = '';

}, 2000);

} catch (err) {

showInlineMessage('Could not copy link. Please copy manually.', 'generatedLink');

}


document.body.removeChild(tempTextarea);

}


function proceedToDifficulty() {

document.getElementById('linkDisplayScreen').style.display = 'none';

document.getElementById('menuScreen').style.display = 'flex';

}


function showInlineMessage(message, nearElementId) {

const existingMsg = document.querySelector('.inline-error-message');

if (existingMsg) existingMsg.remove();


const msgDiv = document.createElement('div');

msgDiv.className = 'inline-error-message';

msgDiv.textContent = message;

msgDiv.style.cssText = 'color: #ef4444; font-size: 16px; margin-top: 10px; text-align: center; background: rgba(239, 68, 68, 0.2); padding: 10px; border-radius: 5px; border: 1px solid #ef4444;';


const element = document.getElementById(nearElementId);

if (element && element.parentElement) {

element.parentElement.insertBefore(msgDiv, element.nextSibling);

}


setTimeout(() => msgDiv.remove(), 3000);

}


let gameState = {

score: 0,

lives: 3,

asteroids: [],

gameRunning: false,

asteroidSpeed: 1,

spawnRate: 2000,

difficulty: 'medium',

baseSpeed: 1

};


const difficultySettings = {

easy: { speedMultiplier: 0.5, spawnRate: 3000 },

medium: { speedMultiplier: 1, spawnRate: 2000 },

hard: { speedMultiplier: 2, spawnRate: 1500 }

};


const gameContainer = document.querySelector('.game-container');

const scoreElement = document.getElementById('score');

const livesElement = document.getElementById('lives');

const wordInput = document.getElementById('wordInput');

const translationElement = document.getElementById('translation');

const gameOverElement = document.getElementById('gameOver');

const finalScoreElement = document.getElementById('finalScore');

const menuScreen = document.getElementById('menuScreen');


function startGameWithDifficulty(difficulty) {

gameState.difficulty = difficulty;

const settings = difficultySettings[difficulty];

gameState.baseSpeed = settings.speedMultiplier;

gameState.asteroidSpeed = settings.speedMultiplier;

gameState.spawnRate = settings.spawnRate;


document.getElementById('menuScreen').style.display = 'none';

gameState.gameRunning = true;

wordInput.focus();

startGame();

}


function startGame() {

gameState.score = 0;

gameState.lives = 3;

gameState.asteroids = [];

scoreElement.textContent = gameState.score;

livesElement.textContent = gameState.lives;

gameOverElement.style.display = 'none';


setInterval(createAsteroid, gameState.spawnRate);

setInterval(moveAsteroids, 30);

}


function createAsteroid() {

if (!gameState.gameRunning) return;


const word = getRandomWord();

const asteroid = document.createElement('div');

asteroid.className = 'asteroid';


asteroid.textContent = word.chinese;

asteroid.dataset.word = word.chinese;

asteroid.dataset.translation = word.english;


const x = Math.random() * (window.innerWidth - 80);

asteroid.style.left = x + 'px';

asteroid.style.top = '-80px';


gameContainer.appendChild(asteroid);

gameState.asteroids.push({

element: asteroid,

word: word.chinese,

pinyin: word.pinyin,

translation: word.english,

x: x,

y: -80

});


if (gameState.asteroids.length === 1) {

translationElement.textContent = `Destroy: "${word.english}"`;

}

}


function moveAsteroids() {

if (!gameState.gameRunning) return;


gameState.asteroids.forEach((asteroid, index) => {

asteroid.y += gameState.asteroidSpeed;

asteroid.element.style.top = asteroid.y + 'px';


if (asteroid.y > window.innerHeight - 200) {

asteroid.element.remove();

gameState.asteroids.splice(index, 1);

gameState.lives--;

livesElement.textContent = gameState.lives;


updateTranslation();


if (gameState.lives <= 0) {

endGame();

}

}

});

}


function updateTranslation() {

if (gameState.asteroids.length > 0) {

translationElement.textContent = `Destroy: "${gameState.asteroids[0].translation}"`;

} else {

translationElement.textContent = '';

}

}


function destroyAsteroid(inputPinyin) {

inputPinyin = inputPinyin.trim().toLowerCase().replace(/\s+/g, ' ');


const asteroidIndex = gameState.asteroids.findIndex(a => a.pinyin.toLowerCase().replace(/\s+/g, ' ') === inputPinyin);

if (asteroidIndex !== -1) {

const asteroid = gameState.asteroids[asteroidIndex];


createLaserBeam(asteroid);


setTimeout(() => {

asteroid.element.classList.add('exploding');

}, 100);


setTimeout(() => {

asteroid.element.remove();

}, 600);


gameState.asteroids.splice(asteroidIndex, 1);

gameState.score += 10;

scoreElement.textContent = gameState.score;


if (gameState.score % 100 === 0) {

gameState.asteroidSpeed += (0.5 * gameState.baseSpeed);

}


updateTranslation();

return true;

}

return false;

}


function createLaserBeam(asteroid) {

const laser = document.createElement('div');

laser.className = 'laser-beam';


const earthCenterX = window.innerWidth / 2;

const earthCenterY = window.innerHeight - 150;


const asteroidCenterX = asteroid.x + 40;

const asteroidCenterY = asteroid.y + 40;


const distance = Math.sqrt(Math.pow(asteroidCenterX - earthCenterX, 2) + Math.pow(asteroidCenterY - earthCenterY, 2));

const angle = Math.atan2(asteroidCenterY - earthCenterY, asteroidCenterX - earthCenterX);


laser.style.height = distance + 'px';

laser.style.left = earthCenterX + 'px';

laser.style.bottom = (window.innerHeight - earthCenterY) + 'px';

laser.style.transform = `rotate(${angle}rad)`;

laser.style.transformOrigin = 'bottom center';


gameContainer.appendChild(laser);


setTimeout(() => {

laser.remove();

}, 300);

}


wordInput.addEventListener('input', function(e) {

const inputValue = e.target.value;

if (destroyAsteroid(inputValue)) {

e.target.value = '';

}

});


function endGame() {

gameState.gameRunning = false;

finalScoreElement.textContent = gameState.score;

gameOverElement.style.display = 'block';

}


function restartGame() {

gameState.asteroids.forEach(asteroid => asteroid.element.remove());

gameState.asteroids = [];

gameState.gameRunning = true;

gameState.asteroidSpeed = gameState.baseSpeed;

startGame();

}

</script>

<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9b7f3902943316a2',t:'MTc2NzQwODk4My4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>

</html>
