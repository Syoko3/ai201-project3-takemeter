# TakeMeter - Project 3

---

## Demo Video

Link: 

---

## Community Choice & Reasoning

I chose baseball subreddits because this community contains some posts based on baseball game live highlights and some breaking news on Major League Baseball. This is a good fit for a classification task because it contains hard data and subjective freedom. The discourse is varied enough to be interesting by highly technical, statistic-driven "sabermetric" analysis to immediate, emotional reactions during live game threads.

---

## Label Taxonomy

| Labels | Definition of Label | Example Post #1 | Example Post #2 |
|--------|-------------------------|------------------------------|------------------------------|
| Media & Highlights | Direct video clips of gameplay or in-game events. | Padres extend their lead to five with a Jackson Merrill towering 2-run shot in the 9th | The Rays take the lead and drop a 4-run 5th inning on Shohei Ohtani |
| News & Official | Direct links to reports, signings, transactions, or injury updates from recognized media or MLB sources. | [MLBTR] Braves To Select Carlos Carrasco, Jair Camargo | [Stebbins] Out in Milwaukee, the Guardians recalled Kahlil Watson from Triple-A Columbus while placing Chase DeLauter on the 10-day injured list |
| Facts & Analysis | Structured arguments supported by specific, verifiable statistical evidence (e.g., WAR, ERA+, historical trends), including fun facts. | Brett Kerry of the Angels just recorded a 5 pitch scoreless inning whilst also committing two errors | On this date in 1960, Ted Williams became the 4th member of the 500 HR club — here's what the leaderboard looked like on 6/17/1960 |
| Discussions & Opinions | Subjective discussions, opinions, or "hot takes". | Has anyone seen an mlb sculpture that is a good likeness of its subject? | Adjustments after breaking Hamate |

---

## Data Collection

**Data Collection Source:** r/baseball
**Labeling Process:** 
**Label Distribution:** 
**3 Difficult-to-label Examples:**
- 
- 
- 

---

## Fine Tuning Approach



---

## Baseline Description



---

## Full Evaluation Report

**Model Metrics:**

| Metric Class Name | Model #1 Performance | Model #2 Performance |
|-------|----------------------|----------------------|
|  |  |  |
|  |  |  |

**Specific Wrong Predictions & Analysis:**

| Post | Model 1 Prediction & Confidence | Model 2 Prediction & Confidence | Status | Analysis | One Correct Example |
|------|---------------------------------|---------------------------------|--------|---------------------|------------------|
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

**Confusion Matrix:**



---

## Model Reflection



---

## Spec Reflection



---

## AI Usage

**Instance 1**

- *What I gave the AI:*
- *What it produced:*
- *What I changed or overrode:*

**Instance 2**

- *What I gave the AI:*
- *What it produced:*
- *What I changed or overrode:*

---

## Notes (I will delete later)

🎯 Baseline accuracy: 0.806  (evaluated on 36/36 parseable responses)

Per-class metrics (baseline):
                        precision    recall  f1-score   support

    Media & Highlights       0.94      0.94      0.94        18
       News & Official       0.58      0.88      0.70         8
      Facts & Analysis       1.00      0.57      0.73         7
Discussions & Opinions       0.50      0.33      0.40         3

              accuracy                           0.81        36
             macro avg       0.76      0.68      0.69        36
          weighted avg       0.84      0.81      0.80        36

<!--- Reflect briefly: where did the baseline struggle? Are there specific labels it consistently confuses? Write down your hypothesis — you'll test it after fine-tuning. --->

Wrong predictions: 18 / 36

--- #1 ---
Text:      [TJ Stats] Outs Above Average Leaders - Outfielder
True:      Facts & Analysis
Predicted: Media & Highlights  (confidence: 0.31)

--- #2 ---
Text:      Do player's contracts pause if we have a full season lockout next year?
True:      Discussions & Opinions
Predicted: Facts & Analysis  (confidence: 0.28)

--- #3 ---
Text:      The Red Sox had 13 on base tonight. They lost 3-0.
True:      Facts & Analysis
Predicted: Media & Highlights  (confidence: 0.31)

--- #4 ---
Text:      Gerrit Cole throws a quality start against the White Sox on the back of 11 runs of run support: 6 IP, 3 H, 2 ER, 2 BBs, 6 Ks. Season ERA of 2.57
True:      Facts & Analysis
Predicted: Media & Highlights  (confidence: 0.33)

--- #5 ---
Text:      [Kowatsch] Julio Rodriguez exits the game before the top of the seventh. Victor Robles moves to center field and Rob Refsnyder in at right.
True:      News & Official
Predicted: Media & Highlights  (confidence: 0.35)

--- #6 ---
Text:      [Seidler] The Seattle Mariners select the contract of Curtis Washington Jr. from Everett AquaSox. As far as I can tell they needed an emergency OF for tonight, could physically only get a player from ...
True:      News & Official
Predicted: Media & Highlights  (confidence: 0.29)

--- #7 ---
Text:      [Gelb] Phillies optioned Andrew Painter after the game. Theyll bring an extra reliever for Thursday, then try something different next week with No. 5 spot in rotation.
True:      News & Official
Predicted: Media & Highlights  (confidence: 0.33)

--- #8 ---
Text:      [Gelb] Phillies signed old friend Kolby Allard to a minor-league deal. Hes going to Triple A.
True:      News & Official
Predicted: Media & Highlights  (confidence: 0.30)

--- #9 ---
Text:      [Britton] Francisco Lindor and Tyrone Taylor will start rehab assignments tomorrow with Binghamton.
True:      News & Official
Predicted: Media & Highlights  (confidence: 0.28)

--- #10 ---
Text:      [Talkin baseball] Randy Arozarena heads to the injured list with hamstring soreness in the midst of the very good season he's having
True:      News & Official
Predicted: Media & Highlights  (confidence: 0.29)

--- #11 ---
Text:      A politician in Memphis argued against renovations of the local baseball stadium by saying "People are playing pickleball" instead
True:      News & Official
Predicted: Media & Highlights  (confidence: 0.27)

--- #12 ---
Text:      It appears the 2026 MLB All-Star Game hats have leaked thru an ad on TikTok
True:      Discussions & Opinions
Predicted: Media & Highlights  (confidence: 0.27)

--- #13 ---
Text:      [Matheson] Anthony Santander is scheduled to start hitting "either this weekend or next", John Schneider said. So, sometime soon. "There's a shot he could definitely be a factor." Long road from here,...
True:      Discussions & Opinions
Predicted: Media & Highlights  (confidence: 0.30)

--- #14 ---
Text:      Eduardo Rodriguez's final line against the Angels: 7.0 IP 1R/ER 1HR, 3BB, 5K
True:      Facts & Analysis
Predicted: Media & Highlights  (confidence: 0.33)

--- #15 ---
Text:      [CloseCallSports] Explains the "Contreras Rule" in relation to José Caballero's pitch clock "antics" and warning given by ump in Sunday's game against the Blue Jays
True:      Facts & Analysis
Predicted: Media & Highlights  (confidence: 0.30)

==================================================
RESULTS COMPARISON
==================================================
Model                               Accuracy
---------------------------------------------
Zero-shot baseline (Groq)              0.806
Fine-tuned DistilBERT                  0.500
---------------------------------------------

Fine-tuning regression: 0.306

Use these numbers in your README evaluation report.