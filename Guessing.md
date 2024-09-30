```mermaid
---
title: Flowgorithm
---
flowchart TD
State[State] --- Text([Prompt]) ---Decision{Decision}
StartState[Start] --> WelcomeTxt([Welcome Player])
QuitGame[Quit]
 WelcomeTxt --> PlayChoice{Play Game?}
    PlayChoice -->|Yes| MinPrompt
    PlayChoice -.->|No| QuitGame

    MinPrompt([Prompt Min Value])
    MinPrompt --> IsMinValid{Valid Minimum?}
        IsMinValid -.->|No|MinPrompt
        IsMinValid -->|Yes|MaxPrompt
        

    MaxPrompt([Prompt Max Value])
    MaxPrompt --> IsMaxValid{Valid Maximum?}
        IsMaxValid -.->|No| MaxPrompt
        IsMaxValid -->|Yes| GenerateNum

    GenerateNum[Generate Number X]
    GenerateNum --> PromptGuess
    
    PromptGuess([Prompt Guess Number])
    PromptGuess --> IsPlayerRight

    IsPlayerRight{Is Player Correct?}
    IsPlayerRight -.->|No| PlayerHint
    IsPlayerRight -->|Yes| Congrats

    PlayerHint{Is number greater or lesser than guess?}
        PlayerHint -->|X > Guess| HintLo([Guess was too low])
        PlayerHint -->|X < Guess| HintHi([Guess was too high])
        HintLo --> PromptGuess
        HintHi --> PromptGuess

    Congrats([Congratulations!])
    Congrats --> PlayAgain{Play Again?}
    PlayAgain -->|Yes| MinPrompt
    PlayAgain -.->|No| QuitGame

```
