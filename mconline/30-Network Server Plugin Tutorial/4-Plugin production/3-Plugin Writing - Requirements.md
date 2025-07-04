# Plug-in Writing - Requirements 

Before we start writing a plug-in, we need to first clarify what functions the plug-in needs, what the specific details are, and various API requirements and event requirements for secondary development. 

In the following section, we will take the lottery plug-in as an example and follow the process to make a complete plug-in. 

## Plug-in Requirements 

One lottery is held every day, and each player can randomly receive 3 different numbers, ranging from 1 to 10000, until all are claimed. The lottery is drawn at 20:00 every day, and the winning players are notified and rewards are issued via email (official neteaseAnnounced plug-in). 

## Detailed Requirements 

- Players can enter cp1 to receive the number in the game server or lobby server. After successfully receiving it, the official neteaseAlert plug-in prompts "The number received this time is %s" 
- The reward number is reset after the daily lottery, and players can receive it again. 
- If the upper limit of the number that can be collected on the day is exceeded: 3, when entering cp1 to collect, the official neteaseAlert plug-in prompts "The number collected today has exceeded the upper limit" 
- Before the daily lottery time (20:01 on the previous day to 20:00 on the current day), enter cp2 to check the numbers that have been collected. 
- The official neteaseAlert plug-in prompts the situation of the numbers that have been collected "Today, %s (number) numbers have been collected: %s, %s, %s" 
- 5 numbers are randomly selected from 1~10000 as the winning numbers for this period. 
- Winning email prompt: The winning numbers for this period: %s, %s, %s, %s, %s. Congratulations, you won the prize in this lottery, please keep up the good work. Email attachment content: Obsidian*5 
- Email prompt for those who did not win: The winning numbers for this period: %s, %s, %s, %s, %s. Unfortunately, you did not win the prize in this lottery, please keep up the good work. Email attachment content: Iron ingot*3 
- Players who did not receive any number on the day do not need to send emails. 

## API requirements 

- Give the specified player a random number (must be a number that has not been received in this activity, if there is no number, return -1) 
- Return the number of numbers the player has obtained 
- Return the list of numbers the player has obtained 
- Reset a player's number 
- Reset all numbers 
- Execute the award, return the list of winning numbers and the list of winning players 

## Event requirements 

- Triggered before the award time - return the winning number, the winning number can be modified 
- Triggered after the award time - return the winning number and the winning player 

