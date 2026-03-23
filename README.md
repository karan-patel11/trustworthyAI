# trustworthyAI

A repo investigating when and how large language models fail in high-stakes domains. Each project uses a different domain to expose a different category of AI failure, from rule integrity to clinical responsibility.

All three projects are self-contained. Start with any one.

---

## Projects

### Project 1: When Empathy Becomes Risky
**Domain: Mental Health Support**  
**File: [Project1.md](./Project1.md)**

Generative AI is increasingly used for emotional support, but it lacks clinical training, situational awareness, and legal accountability. This project documents three failure modes observed when a distressed user prompt was escalated through a generative AI system: incomplete crisis escalation, risk-minimizing reinterpretation of suicidal language, and reinforcement of maladaptive coping behaviors. The findings show that AI harm in sensitive domains does not require explicitly dangerous advice. Subtle framing choices and empathetic overreach are enough.

---

### Project 2: Caught in the Act
**Domain: Game-Playing and Rule Following**  
**File: [Project2.md](./Project2.md)**

Games create a ground truth oracle for testing AI trustworthiness because the rules are unambiguous and violations are provable. This project documents three confirmed, reproducible failures from GPT o3-mini across Tic-Tac-Toe and Poker: evaluating a physically impossible hand without flagging the duplicate card, accepting an illegal rule change that broke the game's win conditions, and confabulating game state under pressure. Each failure is documented with the exact prompt used and a screenshot of the response.

---
### Project 3: Selective Truthiness: Does GPT Tell Different People Different Things?

**Domain: Scientific Communication and Epistemic Fairness**  

**File: [Project3.md](./Project3.md)**

This project tests whether a large language model gives the same factual answer to the same scientific question when the asker’s identity changes. Across eight personas and multiple fresh-thread runs, the results show that the model systematically changes which facts it includes, omits, softens, or expands depending on who appears to be asking. The domain is cannabis effects on the brain and body, but the deeper issue is broader: factual completeness should not depend on persona. 

---

## The Common Thread

These three projects target different domains but expose the same underlying issue. Large language models are optimized to produce responses that feel correct and helpful. What they do not do reliably is validate whether the task they are being asked to perform should be performed at all, whether the inputs they are being given are legitimate, and whether the facts they provide remain consistent across contexts and users.

In mental health, that gap produces empathetic responses that quietly steer users away from care. In games, it produces confident evaluations of impossible scenarios. In scientific communication, it produces different levels of factual completeness depending on who is asking. The domain changes. The failure mode does not.

---

## Repo Structure

```
trustworthyAI/
├── README.md          
├── Project1.md        # Mental health AI failure analysis
├── Project2.md        # Game-playing rule violation analysis
└── LICENSE
```

---

*Research conducted February-March 2026. Author: karan-patel11.*
