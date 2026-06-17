Open challenge code structure
====
### 1. Open Challenge: Main Control Flow
The following flowchart illustrates the discrete state logic (Bang-Bang controller) combined with the lap-counting thread.

#### Logic Flowchart (Mermaid)
```mermaid
graph TD
    Start([Начало]) --> Init[line = 0]
    Init --> Wait1[Wait 1 second]
    Wait1 --> Sound1[EV3 Sound: Start Tone]
    Sound1 --> InitMotors[Motor D speed = 100<br>Motor A speed = 100]
    InitMotors --> LoopStart
    
    LoopStart[Motor D: Вперед<br>против часовой] --> DistCheck{УЗ Датчик<br>Порт 2 < 40 см?}
    
    DistCheck -- Да --> SteerLeft[Motor A: Налево<br>против часовой]
    DistCheck -- Нет --> SteerRight[Motor A: Направо<br>по часовой]
    
    SteerLeft --> LightCheck
    SteerRight --> LightCheck
    
    LightCheck{Датчик цвета<br>Порт 4 < 20%?}
    LightCheck -- Нет --> LoopStart
    LightCheck -- Да --> DebounceWait[Wait 1 second]
    
    DebounceWait --> SoundLine[EV3 Sound: Blue]
    SoundLine --> LineAdd[line = line + 1]
    LineAdd --> StopCheck{line == 12?}
    
    StopCheck -- Нет --> LoopStart
    StopCheck -- Да --> StopDrive[Остановить Motor D]
    
    StopDrive --> SoundEnd[EV3 Sound: Game Over]
    SoundEnd --> FinalWait[Wait 1 second]
    FinalWait --> Stop[Stop Program]
    Stop --> End([Конец])
