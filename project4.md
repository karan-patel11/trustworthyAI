# When AI Knows the Answer But Can't Stop Talking: Testing GPT o3's Common-Sense Reasoning

**By Karan Patel | CSCI 6907 – Trustworthy AI | George Washington University | April 2026**

---

## Why Common Sense Is the Right Stress Test

GPT o3 can pass the bar exam, write production-ready code, and summarize a 50-page research paper in seconds. So I decided to ask it something much simpler: what should you do when someone sneezes during a job interview?

The answer is obvious. You say "bless you" and move on. Any ten-year-old knows this. What GPT o3 produced instead was a 600-word response with two tables, a numbered etiquette guide, edge cases for video and panel interviews, and a public health note citing the CDC.

That gap, between knowing the right answer and knowing when to stop, is what this project is actually about.

Common-sense reasoning is one of the most honest stress tests for AI trustworthiness. Not because it catches hallucinations or logical errors, but because it tests something harder to measure: whether a model understands context well enough to know what a situation actually requires. For this project, I designed ten prompts across five categories — physical intuition, temporal reasoning, social norms, causal inference, and pragmatic ambiguity, and ran them through GPT o3 (via ChatGPT, April 2026). I wanted to see not just whether it got things right, but whether it responded like something you could actually rely on.

---

## The Experiment

### Category 1: Physical Intuition

**Prompt 1:** *"I left a chocolate bar on my car's dashboard on a sunny July afternoon in Virginia. When I came back two hours later, what did I find?"*

GPT led with "A puddle of chocolate" direct, correct, no fluff. It followed up with a brief explanation about cabin temperatures exceeding 120°F in Virginia summers, well above chocolate's melting point. Short, accurate, useful.


![SS9_chocolate_bar_and_friend_text](https://github.com/user-attachments/assets/055107a9-3909-44fd-b8e2-0f0d79d59b46)

**Verdict: PASS.** This is what a good response looks like. Answer first, brief explanation after. No hedging, no unnecessary depth.

---

**Prompt 2:** *"If I drop a bowling ball and a feather from the same height in my living room, which hits the ground first? What if I do it on the Moon?"*

GPT correctly said the bowling ball lands first on Earth because of air resistance, and that both land at the same time on the Moon because there's essentially no atmosphere. It even referenced the Apollo 15 demonstration where astronaut David Scott dropped a hammer and feather side by side.


![SS1_bowling_ball_feather](https://github.com/user-attachments/assets/e262774c-b65f-47ad-806d-193874b803b7)

**Verdict: PASS.** It correctly switched reasoning between two different physical contexts — practical Earth vs. idealized Moon conditions. Solid.

---

### Category 2: Temporal Reasoning

**Prompt 3:** *"I put a load of laundry in the washing machine before leaving for a 3-day weekend trip. What's the state of the laundry when I return?"*

The real answer here is simple: your clothes are going to smell terrible. Re-wash them. That's it. Instead, GPT produced a three-column table covering "What you'll notice / Why it happened / How to fix it," a section explaining the microbiology of mildew growth, and four preventive tips for next time — including advice about leaving the washer door ajar and using delay-start features.


![SS2_laundry](https://github.com/user-attachments/assets/8ba4d83d-3302-458e-8ebe-78065d4b149a)

**Verdict: PARTIAL FAIL.** GPT knew the answer. It just couldn't leave it at that. Nobody who asked this question wanted a washer maintenance guide. The right answer was there — it was just buried.

---

**Prompt 4:** *"My friend texted me 'I'll be there in 5 minutes' forty-five minutes ago. Should I start worrying, or is this normal?"*

GPT correctly recognized that "I'll be there in 5 minutes" is basically everyone's way of saying "I left the house." Totally normal. But then it built out a full delay scenario table, a four-point checklist for when to actually start worrying, and recommendations about sharing live location via app to avoid future confusion.


![SS9_chocolate_bar_and_friend_text](https://github.com/user-attachments/assets/3369be8b-fdb0-400e-abda-664c1db664fe)

**Verdict: PARTIAL FAIL.** It got the tone of the situation right but then responded like it was training a crisis hotline worker. A friend would say "send a nudge, they probably got stuck in traffic." GPT handed you a protocol.

---

### Category 3: Social Norms

**Prompt 5:** *"I'm at a job interview. The interviewer sneezes. What should I do?"*

This one is the centerpiece of the whole experiment. The answer is "bless you, carry on." GPT produced: a four-step numbered guide to handling the sneeze, a table of professional etiquette principles with four rows, a second table covering special cases (video interviews, panel interviews, culturally different settings), a "what to avoid" bullet list, and a health note citing the CDC about droplet transmission.


![SS3_interview_sneeze](https://github.com/user-attachments/assets/8b2c32b5-3357-4fdc-93fd-1d425e842bde)

**Verdict: CLEAR FAIL.** This is the most revealing result of the ten. The question needed a reflex. GPT gave a framework. In a real deployment — an interview prep assistant, a workplace chatbot — this response would not just be unhelpful, it would actively get in the way. The user needed four words. They got a document.

---

**Prompt 6:** *"My roommate cooked dinner for both of us. The food tastes terrible. What should I say?"*

GPT gave a four-step "tactful, honest approach" with example phrases at each step, a "Why this works" table analyzing the psychological purpose of thanking someone for dinner, a "What to avoid" list, and a one-line fallback option.


![SS4_roommate_bad_food](https://github.com/user-attachments/assets/c0649159-68f4-4447-991d-679e490f0df3)

**Verdict: PARTIAL FAIL.** The advice is technically fine. But nobody sits down to a bad meal and thinks through a four-step conflict resolution framework. Real common sense here is: say thanks, eat what you can, don't bring it up unless they ask. GPT knows the rule but applies it like a training manual, not like a person.

---

### Category 4: Causal Inference

**Prompt 7:** *"Every morning, my neighbor's dog barks at exactly 6:15 AM. My alarm is set for 6:15 AM. Did the dog learn my alarm schedule?"*

GPT opened with "Probably not" and correctly identified this as a coincidence or Pavlovian association with a shared environmental trigger. It listed four alternative explanations — the neighbor's own routine, environmental cues like garbage trucks, the dog's circadian rhythm, and possible sound association — and suggested a practical test: shift your alarm by five minutes and see if the barking shifts with it.


![SS5_dog_barking](https://github.com/user-attachments/assets/a0e888a1-5e6d-4877-8966-af68b1fdcda4)

**Verdict: PASS.** This is GPT at its best. It rejected the implied causal link, offered real alternative explanations, and even suggested how you'd actually test it. Causal reasoning in structured scenarios is clearly a strength.

---

**Prompt 8:** *"I watered my plant every day for a month, and it died. My friend never waters her plant, and it's thriving. Does this mean watering kills plants?"*

GPT immediately pushed back on the false conclusion. It explained overwatering as a common cause of plant death, discussed how different species have different water needs, and noted micro-environment factors like soil type and pot drainage that affect the comparison.


![SS6_watering_plant](https://github.com/user-attachments/assets/5044a707-99f2-4383-94c7-1c6d79b96a06)

**Verdict: PASS.** It didn't take the bait of the misleading framing. Identified the confounding variables, gave a reasonable explanation, stayed on topic.

---

### Category 5: Pragmatic Ambiguity

**Prompt 9:** *"I asked my professor if the exam is hard. She said 'You'll be fine.' Should I study?"*

GPT correctly identified that "You'll be fine" is a polite non-answer, not a guarantee — professors say it to be encouraging, not to tell you to skip studying. Good. Then it generated a six-step study plan with time estimates per step.
![SS7_professor_youll_be_fine](https://github.com/user-attachments/assets/9c29d5a8-f55d-4693-944a-e03942a5924a)


**Verdict: PARTIAL FAIL.** The question was about interpreting an ambiguous social phrase. GPT interpreted it correctly and then kept going for another 400 words. Nobody asked for a study plan. The overshooting is the problem, not the core answer.

---

**Prompt 10:** *"A sign outside a restaurant says 'Best Pizza in Town.' Is it actually the best pizza in town?"*

GPT correctly called it marketing puffery — a broad, unverifiable claim. It explained that U.S. advertising law allows superlative claims because regulators treat them as opinion, not fact. It suggested ways you might actually verify pizza quality through independent reviews and blind comparisons.


![SS8_best_pizza_sign](https://github.com/user-attachments/assets/cb1b6a5c-a101-4370-988d-c8c245f10f65)


**Verdict: PASS.** Appropriate skepticism, accurate reasoning, stayed proportional.

---

## What I Actually Found

After running all ten, one pattern dominated everything else.

**GPT o3 does not fail at facts. It fails at knowing when enough is enough.**

Five of the ten prompts, the social and temporal ones, triggered the same behavior: GPT identified the right answer and then kept producing content well past the point where it was useful. The sneeze prompt is the starkest example. A four-word answer became a structured document. But it showed up across the laundry prompt, the late friend prompt, the bad food prompt, and the study plan prompt too. It wasn't random, it was consistent.

The causal reasoning prompts went the other way. Both passed cleanly. GPT didn't fall for the dog-alarm coincidence or the watering-kills-plants framing. It identified confounding variables, suggested ways to actually test the claims, and stayed appropriately scoped. This is worth noting honestly, the model has real strengths in structured logical reasoning.

The third pattern sits between those two: prompts where GPT got the core answer right and then attached something nobody asked for. The professor prompt is the clearest case. "You'll be fine" means study anyway — GPT got that. Then it built a six-step study plan. The judgment was correct. The scope was off.

---

## Why This Matters for Trustworthy AI

The obvious AI safety concerns are hallucinations, bias, and factual errors. Those are real. But what these ten prompts surfaced is a different problem that gets much less attention: **a model that buries the right answer under noise is not trustworthy, even if it's technically correct.**

Think about where AI assistants actually get deployed, customer service bots, interview prep tools, medical triage assistants, elder care applications. In those contexts, a 600-word response to a four-word question doesn't just waste time. It shifts the cognitive burden back onto the user to find what matters. In a high-stakes moment, that failure has real consequences.

There's also a subtler issue with social reasoning. GPT knows social norms, it has clearly been trained on enough human interaction to retrieve the right rules. But it doesn't feel the weight of them the way people do. When you're at a dinner table and the food is bad, you don't run a four-step protocol, you make a judgment in a fraction of a second based on years of social experience. GPT has the knowledge without the instinct. For applications where natural, human-feeling interaction actually matters, that gap is significant.

One more thing worth flagging: o3 is a reasoning model, explicitly designed to think longer before responding. In these prompts, more thinking didn't mean better calibration, it meant more thorough responses to questions that didn't need thoroughness. That's a specific concern for anyone evaluating whether reasoning models are the right fit for conversational AI applications. More compute doesn't automatically mean more appropriate.

This connects to something I noticed in earlier experiments, in adversarial testing and persona-sensitivity work I did for this course — that the most dangerous AI failures aren't the obvious ones. They're the ones where the model is almost right, almost human, but just slightly off in a way users don't immediately notice. Proportionality failure fits that description exactly. It's subtle enough to miss, consistent enough to matter at scale.

---

## Conclusion

GPT o3 passed six of ten prompts and partially failed four. It didn't hallucinate, it didn't get confused by basic logic, and it correctly handled every factual question I threw at it. By standard benchmarks, this looks like a strong performance.

But the consistent failure across social prompts tells a different story. The model knows what to do, it just doesn't know when to stop. In real-world deployment, that distinction matters more than it does on a leaderboard. Users don't need exhaustive coverage. They need the right answer at the right size, fast enough to actually use.

Building trustworthy AI means evaluating calibration, not just correctness. Until that's part of how we measure these systems, we'll keep shipping models that ace the tests and fumble the obvious stuff.

---

*Published for CSCI 6907: Trustworthy AI, Spring 2026, The George Washington University.*
