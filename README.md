# TakeMeter - Project 3

---

## Demo Video

Link: 

---

## Community Choice & Reasoning

I chose baseball subreddits because this community contained some posts based on baseball game live highlights and some breaking news on Major League Baseball. This was a good fit for a classification task because it included hard data and subjective freedom. The discourse was varied enough to be interesting by highly technical, statistic-driven "sabermetric" analysis to immediate, emotional reactions during live game threads.

---

## Label Taxonomy

| Labels | Definition of Label | Example Post #1 | Example Post #2 |
|--------|-------------------------|------------------------------|------------------------------|
| Media & Highlights | Direct video clips of gameplay or in-game events. | Padres extend their lead to five with a Jackson Merrill towering 2-run shot in the 9th | The Rays take the lead and drop a 4-run 5th inning on Shohei Ohtani |
| News & Official | Direct links to reports, signings, transactions, or injury updates from recognized media or MLB sources. | [MLBTR] Braves To Select Carlos Carrasco, Jair Camargo | [Stebbins] Out in Milwaukee, the Guardians recalled Kahlil Watson from Triple-A Columbus while placing Chase DeLauter on the 10-day injured list |
| Facts & Analysis | Structured arguments supported by specific, verifiable statistical evidence (e.g., WAR, ERA+, historical trends), including fun facts and player's data of today's game without video clips. | Brett Kerry of the Angels just recorded a 5 pitch scoreless inning whilst also committing two errors | On this date in 1960, Ted Williams became the 4th member of the 500 HR club — here's what the leaderboard looked like on 6/17/1960 |
| Discussions & Opinions | Subjective discussions, questions, hypotheses, opinions, or "hot takes". | Has anyone seen an mlb sculpture that is a good likeness of its subject? | Do player's contracts pause if we have a full season lockout next year? |

---

## Data Collection

- **Data Collection Source:** r/baseball
- **Labeling Process:** I classified the total of 240 posts from baseball subreddits in 4 labels based on the label definitions from the "Label Taxonomy" section above. I also added notes on some posts for any difficult cases that are hard to classify. I also used ChatGPT to pre-label the first 50 posts with difficult cases explained, and I reviewed and corrected them by using two columns, "label" for my verified label and "label_by_model" for pre-labeled ones.
- **Label Distribution:** I had 120 posts on "Media & Highlights", 50 post on "News & Official", 50 posts on "Facts & Analysis", and 20 posts on "Discussions & Opinions". There were high frequency of "Media & Highlights" (50%) because many of the posts included video clips of in-game events. "Discussions & Opinions" were the lowest frequency (8.3%) because there were only high-effort subjective threads included in the baseball subreddits. After collecting 200 posts, I saw "News & Official" was underrepresented, so I added 40 more posts, including some posts for "Media & Highlights" to match the expected number of posts that I specified in Data Collection Plan section of planning.md, and some posts for "Discussions & Opinions" to avoid underrepresentation.
- **3 Difficult-to-label Examples:**

| Example Post | Two labels that sit at the boundary | Notes |
|-----------------------------|----------------------|-----------------------------------|
| [CloseCallSports] Explains the "Contreras Rule" in relation to José Caballero's pitch clock "antics" and warning given by ump in Sunday's game against the Blue Jays | "Media & Highlights" vs. "Facts & Analysis" | If the video is the focus, use "Media & Highlights". If the text is the focus, use "Facts & Analysis". |
| The Red Sox are the 2nd time in MLB history since 1898 to leave 13+ runners on base and score 1 or 0 runs in back-to-back games, joining the 1919 Washington Nationals. | "News & Official" vs. "Facts & Analysis" | If it is a simple statement of an event, use "News & Official". If it interprets the event, use "Facts & Analysis". |
| [TJStats] My Top 100 MLB Prospects | "Facts & Analysis" vs. "Discussions & Opinions" | If a specific stat is used to support a logical claim, use "Facts & Analysis". If there is an image that includes statistical information, use "Facts & Analysis". If no stat or evidence is included, use "Discussions & Opinions". |

---

## Fine Tuning Approach

- **Base Model:** distilbert-base-uncased
- **Training Setup:** 
- **Hyperparameter Decisions:** I changed 4 things in hyperparamters. I changed num_train_epochs from 3 to 5, decreased the learning_rate to 5e-5, and increased the weight_decay to 0.10 and warmup_steps to 100.

---

## Baseline Description

The prompt I used was to say to the model that you are classifying the posts from baseball subreddits using the four labels I defined from the Labels section of planning.md. For the examples, I used the example post #1 from "Media & Highlights" and "News & Official" each, and the example post #2 from "Facts & Analysis" and "Discussions & Opinions" each. The results were collected by 

---

## Full Evaluation Report

**Model Per-Class Metrics:**

- Model 1: llama-3.3-70b-versatile (Overall Accuracy: 0.861)
| Label | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Media & Highlights | 1.00 | 0.94 | 0.97 | 18 |
| News & Official | 0.64 | 0.88 | 0.74 | 8 |
| Facts & Analysis | 1.00 | 0.86 | 0.92 | 7 |
| Discussions & Opinions | 0.50 | 0.33 | 0.40 | 3 |

- Model 2: distilbert-base-uncased (Overall Accuracy: 0.889)
| Label | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Media & Highlights | 0.95 | 1.00 | 0.97 | 18 |
| News & Official | 0.70 | 0.88 | 0.78 | 8 |
| Facts & Analysis | 1.00 | 0.86 | 0.92 | 7 |
| Discussions & Opinions | 1.00 | 0.33 | 0.50 | 3 |

**Confusion Matrix:**

![alt_text](outputs/confusion_matrix.png)

**Wrong Predictions & Analysis:**

| Post | Analysis |
|------|--------------------|
|  |  |
|  |  |
|  |  |

**Sample Classifications:**
| Post | Model 1 Prediction | Model 1 Confidence | Model 2 Prediction | Model 2 Confidence |
|------|--------------------|--------------------|--------------------|--------------------|
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |

*One Correct Prediction & Explanation why it is reasonable:*


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

🎯 Baseline accuracy: 0.861  (evaluated on 36/36 parseable responses)

Per-class metrics (baseline):
                        precision    recall  f1-score   support

    Media & Highlights       1.00      0.94      0.97        18
       News & Official       0.64      0.88      0.74         8
      Facts & Analysis       1.00      0.86      0.92         7
Discussions & Opinions       0.50      0.33      0.40         3

              accuracy                           0.86        36
             macro avg       0.78      0.75      0.76        36
          weighted avg       0.88      0.86      0.86        36

🎯 Fine-tuned model accuracy: 0.889

Per-class metrics (fine-tuned model):
                        precision    recall  f1-score   support

    Media & Highlights       0.95      1.00      0.97        18
       News & Official       0.70      0.88      0.78         8
      Facts & Analysis       1.00      0.86      0.92         7
Discussions & Opinions       1.00      0.33      0.50         3

              accuracy                           0.89        36
             macro avg       0.91      0.77      0.79        36
          weighted avg       0.91      0.89      0.88        36

Wrong predictions: 4 / 36

--- #1 ---
Text:      [Kowatsch] Julio Rodriguez exits the game before the top of the seventh. Victor Robles moves to center field and Rob Refsnyder in at right.
True:      News & Official
Predicted: Media & Highlights  (confidence: 0.98)

--- #2 ---
Text:      It appears the 2026 MLB All-Star Game hats have leaked thru an ad on TikTok
True:      Discussions & Opinions
Predicted: News & Official  (confidence: 0.88)

--- #3 ---
Text:      [Matheson] Anthony Santander is scheduled to start hitting "either this weekend or next", John Schneider said. So, sometime soon. "There's a shot he could definitely be a factor." Long road from here,...
True:      Discussions & Opinions
Predicted: News & Official  (confidence: 0.90)

--- #4 ---
Text:      [CloseCallSports] Explains the "Contreras Rule" in relation to José Caballero's pitch clock "antics" and warning given by ump in Sunday's game against the Blue Jays
True:      Facts & Analysis
Predicted: News & Official  (confidence: 0.89)