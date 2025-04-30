# gunting-batu-keras
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scal">
    <title>Rock Paper Scissor Game</title>
    <link rel="stylesheet" href="css/style.css">
</head>

<body>
    <!-- papan score -->
    <div class="papan-score">
        <div class="papan-player">
            <div class="nama-player">Player</div>
            <div id="score-player" class="score-player">0</div>
        </div>
        <div class="papan-computer">
            <div class="nama-computer">Computer</div>
            <div id="score-computer" class="score-computer">0</div>
        </div>
    </div>

    <!-- papan permainan-->
    <div class="papan-permainan">
        <div class="image-player">
            <img id="img-player" src="images/paper-player.jpg" alt="" width="100%">
        </div>
        <div class="image-computer">
            <img id="img-computer" src="images/paper-computer.jpg" alt="" width="100%">
        </div>
    </div>

    <!-- papan button -->
    <div class="papan-button">
        <button class="play-btn" onclick="play('rock')">Rock</button>
        <button class="play-btn" onclick="play('paper')">Paper</button>
        <button class="play-btn" onclick="play('scissor')">Scissor</button>
    </div>

    <script src="js/main.js"></script>
</body>

</html>







const DRAW = 'draw'
const P_WIN = 'player win'
const C_WIN = 'computer win'

let initScorePlayer = 0
let initScoreComputer = 0

let scorePlayer = document.getElementById('score-player')
let scoreComputer = document.getElementById('score-computer')

let imgPlayer = document.getElementById('img-player')

let imgComputer = document.getElementById('img-computer')

let playBtn = document.getElementsByClassName('play-btn')

let imgPath = 'images'

let options = ['rock', 'paper', 'scissor']

function play(option) {
    let playerDecision = setImage(option)
    let comDecision = setImageComputer()
    setTheWinner(option, comDecision)
}

function setImage(option) {
    imgPlayer.src = imgPath+'/'+option+'-player.jpg'

    return option
}

function setImageComputer() {
    let computerDecision = options[Math.floor(Math.random()*options.length)]
    imgComputer.src = imgPath+'/'+computerDecision+'-computer.jpg'

    return computerDecision
}

function setTheWinner(playerDecision, comDecision) {
    let result = ''
    if(playerDecision == 'rock') {
        switch (comDecision) {
            case 'rock':
                result = DRAW
                break;
        
            case 'paper':
                result = C_WIN
                break;        

            case 'scissor':
                result = P_WIN
                break;
        }
    }
        
    if(playerDecision == 'paper') {
        switch (comDecision) {
            case 'rock':
                result = P_WIN
                break;
        
            case 'paper':
                result = DRAW
                break;        

            case 'scissor':
                result = C_WIN
                break;
        }
    }

    if(playerDecision == 'scissor') {
        switch (comDecision) {
            case 'rock':
                result = C_WIN
                break;
        
            case 'paper':
                result = P_WIN
                break;        

            case 'scissor':
                result = DRAW
                break;
        }
    }

    scoring(result)
}

function scoring(result) {
    if(result == 'player win') {
        initScorePlayer++
        scorePlayer.innerHTML = initScorePlayer

        if(initScorePlayer >= 3) {
            for (let i = 0; i < playBtn.length; i++) {
                playBtn[i].setAttribute('disabled', '')
                
            }

        }

    }
    if(result == 'computer win') {
        initScoreComputer++
        scoreComputer.innerHTML = initScoreComputer

        if(initScoreComputer >= 3) {
            for (let i = 0; i < playBtn.length; i++) {
                playBtn[i].setAttribute('disabled', '')
                
            }
            
        }
    }

}



* {
    margin: 0;
    font-family: monospace;
}
.papan-score {
    border: solid;
    display: flex;
    justify-content: center;
    text-align: center;
    color: white;
}
.papan-player {
    background-color: red;
    width: 150px;
}
.papan-computer {
    background-color: blue;
    width: 150px;
}
.nama-player {
    font-size: 22px;
    border-bottom: solid;
    padding: 5px;
}
.nama-computer {
    font-size: 22px;
    border-bottom: solid;
    padding: 5px;
}
.score-player {
    font-size: 25px;
    padding: 5px;
}
.score-computer {
    font-size: 25px;
    padding: 5px;
}


.papan-permainan {
    margin-top: 15px;
    display: flex;
    justify-content: center;
    gap: 55px;
}
.image-player {
    max-width: 450px;
}
.image-computer {
    max-width: 450px;
}
.papan-button {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-top: 25px;
}
.papan-button button {
    padding: 15px;
    width: 120px;
    font-size: 16px;
}
.papan-button button:hover {
    cursor: pointer;
}

C:\Users\USER\Desktop\belajar java script\GAME-SUIT\Images
C:\Users\USER\Desktop\belajar java script\GAME-SUIT\Images\paper-computer.jpg
C:\Users\USER\Desktop\belajar java script\GAME-SUIT\Images\paper-player.jpg
C:\Users\USER\Desktop\belajar java script\GAME-SUIT\Images\rock-computer.jpg
C:\Users\USER\Desktop\belajar java script\GAME-SUIT\Images\rock-player.jpg
C:\Users\USER\Desktop\belajar java script\GAME-SUIT\Images\scissor-computer.jpg
C:\Users\USER\Desktop\belajar java script\GAME-SUIT\Images\scissor-player.jpg
