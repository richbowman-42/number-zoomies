# Number Zoomies — program flow

How the game moves from screen to screen, and how a round loops through problems.
Purple boxes are screens the player sees. Teal boxes are the round loop.

```mermaid
flowchart TD
    open["App opens<br/><small>Load saved players</small>"]
    players["Who's playing?<br/><small>Pick or add a player</small>"]
    backup["Backup<br/><small>Move stats to another device</small>"]
    setup["Setup<br/><small>Ops, range, mode, difficulty</small>"]
    grownups["Grown-ups page<br/><small>Detailed stats</small>"]
    ready["Get ready<br/><small>Mic warm-up if voice is on</small>"]
    problem["Show problem<br/><small>Adaptive or shuffled pick</small>"]
    answer["Answer<br/><small>Type, tap, or say</small>"]
    pause["Pause<br/><small>Clock stops</small>"]
    check{"Right?"}
    right["Score + streak<br/><small>Sparkles at 5, 10, 20</small>"]
    wrong["Streak resets<br/><small>Survival: lose a life</small>"]
    over{"Round over?<br/><small>Sprint clock or lives gone</small>"}
    save["Save stats<br/><small>Facts, families, bests</small>"]
    results["Results<br/><small>Stats and tricky facts</small>"]

    open -->|new device| players
    open -->|returning player| setup
    players <-.-> backup
    players --> setup
    setup <-.-> grownups
    setup -->|Start| ready
    ready --> problem
    problem --> answer
    answer <-.->|Esc or button| pause
    answer --> check
    check -->|yes| right
    check -->|no or time's up| wrong
    right --> over
    wrong --> over
    over -->|no, next problem| problem
    over -->|yes, or Quit| save
    save --> results
    results -->|Play again| ready
    results -->|Practice tricky facts| ready
    results -->|Settings| setup
    setup -->|Switch player| players

    classDef screen fill:#EEEDFE,stroke:#534AB7,color:#26215C
    classDef loop fill:#E1F5EE,stroke:#0F6E56,color:#04342C
    class players,setup,results screen
    class ready,problem,answer,check,right,wrong,over loop
```

## Notes

- **Get ready** locks input until the microphone is in hand, so a permission prompt never eats into the round.
- **Show problem** uses the adaptive picker (tricky facts and weak fact families) at the rate set in Setup; otherwise it draws from a shuffled bag of every fact in range. Drill rounds use only the chosen facts or family.
- In **Survival**, each problem's clock shrinks as the score climbs, tapering toward the difficulty's floor. In **Sprint**, one clock runs for the whole round.
- **Save stats** keeps typed, picked and spoken answer times in separate books, so voice lag and multiple-choice guesses don't skew typed speed.
