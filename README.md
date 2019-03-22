## Contents
* Description
* Features
* Technologies
* Challenges and Solutions
* MVP
* Future Goals
* Author
* Screenshots


## Description
This project is a reimagining of the traditional Black Jack card game themed after the classic painting of dogs playing cards.

## Features
* Uses CSS animation transitions for a more visually engaging gaming experience.
* Keeps track of the number of times both the player and the computer wins to elongate the competitive experience.


## Technologies
* HTML/CSS/JavaScript

## Challenges and Solutions
**Make Cards Flip:** This was the only real challenge I encountered reproducing this classic card game. I created a card holder parent class to hold both the card front and card back images, using a CSS transition to achieve this.

***HTML***
```
 <div class="table">
                    <div class="player-total">0</div>
                    <div class="playerCardHolder">
                        <div class= "card card-1"></div>
                        <div class= "card card-2"></div>
                        <div class= "card card-3"></div>
                        <div class= "card card-4"></div>
                        <div class= "card card-5"></div>
                        <div class= "card card-6"></div>
                    </div>
                    <div class="gameOver scale"></div>
                    
                    <div class="dealer-total">0</div>
                    <div class="dealerCardHolder">
                        <div class= "card card-1"></div>
                        <div class= "card card-2"></div>
                        <div class= "card card-3"></div>
                        <div class= "card card-4"></div>
                        <div class= "card card-5"></div>
                        <div class= "card card-6"></div>
                    </div>
```
***CSS***
```
/* ======================================================================================== Card Imgs  */

.card-holder{
	position: relative;    
    perspective: 400px;
    transform-style: preserve-3d; 
    animation: card-holder 1.5s forwards;
    
    /* backface-visibility: hidden; */
}

.card-front, .card-back{
    position: absolute;
    height: 140px;
	width: 85%;
	top: 0;
    left: 0;
    /* backface-visibility: hidden; */
}

.card-front{
    transform: rotateY(180deg);
}

.card-back{
	/* we are inside of css, go up one with ../ then down into images to get bw */
    background: url('cards/deck.png') no-repeat;
    background-size: contain;
  
}
@keyframes card-holder{
    0%{
        transform: rotateY(0deg) scale(0);
    }
    50%{
        transform: rotateY(0deg) scale(1.5);
    }
    100%{
        transform: rotateY(180deg) scale(1) ;
    }
}
```
***JavaScript***
```
// ======================================================================== PLACE CARD

function placeCard(who,where,what){
    // who = ? ... option 1: 'player', option: 'dealer'
    // where = ? ... option 1-6
    // what = ? ... 1h-13h, 1s-13s, 1d-13d, 1c-13c 
    const classSelector = `.${who}CardHolder .card-${where}`;
    let memoryHTML = ``;


    memoryHTML = `
        <div class="card">
            <div class="card-holder">
                <div class="card-front"><img src="cards/${what}.png" /></div>
                <div class="card-back"></div>
                
            </div>
        </div>`


    $(classSelector).html(memoryHTML);
```

## MVP
Make playable game with user scores.


## Future Goals
Make screen size responsive.

## Authors
- Greg Roques
   - [GitHub Profile](https://github.com/GregRoques)


## Screenshots
![Game Screen](ReadMeImages/1.png)

![Warning Button](ReadMeImages/2.png)

![Game Over](ReadMeImages/3.png)
