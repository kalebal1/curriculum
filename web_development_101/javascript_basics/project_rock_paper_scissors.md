<!-- code by kaleb lyda --!>

<html>
<head>
  <title>Rock Paper Scissors</title>
  <meta charset="UTF-8"/>
</head>
<body>
  <script>

    // determines computer choice by random number generation
    function computerPlay(){
        
        let randomNumber = Math.floor(Math.random() * 3 + 1); //assigns an int 1 to 3
       
        switch(randomNumber){
            case 1:
                return 'rock';
                break;
            case 2:
                return 'scissors';
                break;
            case 3: 
                return 'paper';
                break;
            default:
                break;
        }
    }

    //runs an individual round 
    //param: user's input and randomized computer selection, both strings
    //output: result of round as a string
    function playRound(playerSelection, computerSelection){
        if(playerSelection == null){
            return "Game ended early by player.";
        }
        
        switch(computerSelection){
            case 'rock':
                switch(playerSelection){
                    case 'rock':
                        return "tie! try again";
                        break;
                    case 'paper':
                        playerScore ++;
                        playerWins = true;
                        return "you win! paper beats rock"
                        break;
                    case 'scissors':
                        computerScore ++;
                        return "you lose! rock beats scissors"
                        break;
                    default:
                        return "invalid choice"
                }
                break;
            case 'paper':
                switch(playerSelection){
                        case 'rock':
                            computerScore ++;
                            return "you lose! rock beats paper";
                            break;
                        case 'paper':
                            return "tie! paper vs paper = paper"
                            break;
                        case 'scissors':
                            playerScore ++;
                            playerWins = true;
                            return "you win! scissors beats paper"
                            break;
                        default:
                            return "invalid choice"
                    }
                    break;
            case 'scissors':
                switch(playerSelection){
                            case 'rock':
                                playerScore ++;
                                playerWins = true;
                                return "you win! rock beats scissors";
                                break;
                            case 'paper':
                                computerScore ++;
                                return "you lose! scissors beats paper"
                                break;
                            case 'scissors':
                                return "tie! scissors vs scissors"
                                break;
                            default:
                                return "invalid choice"
                                break;
                        }
                        break;
            default:
                return "invalid choice"
                break;
        }
        
    }

    //compares player scores after 5 rounds
    //param: none
    //output: (to console) winner and scores
    function findWinner(){
        if(playerScore > computerScore){
            console.log("you win! " + playerScore + " to " + computerScore);
        } else if (computerScore > playerScore){
            console.log("you lose :( " + playerScore + " to " + computerScore)
        } else {
            console.log("it's a tie " + playerScore + " to " + computerScore)
        }
    }

    let computerSelection = computerPlay();
    let playerSelection = '';
    let playerScore = 0;
    let computerScore = 0;
    let playerWins = false;

    //this is the room where it happens
    //
    function game(){
        
       
        for(let i = 0; i < 5; i++){
            computerSelection = computerPlay();
            playerSelection = prompt("rock, paper, or scissors?").toLowerCase();
            console.log(playRound(playerSelection, computerSelection));
        }
        findWinner();
    }
    game();


  </script>
</body>
</html>
