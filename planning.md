# TakeMeter - planning.md

---

## Community
<!-- What community did you choose and why? Why is this community a good fit for a classification task — what makes the discourse varied enough to be interesting? -->
I chose baseball subreddits (r/baseball) because this community contains some posts based on baseball game live highlights and some breaking news on Major League Baseball. This is a good fit for a classification task because it contains hard data and subjective freedom. The discourse is varied enough to be interesting by highly technical, statistic-driven "sabermetric" analysis to immediate, emotional reactions during live game threads.

---

## Labels
<!-- What are your 2–4 labels? Define each in a complete sentence. Include 2 example posts per label. -->
| Labels | Definition of Label | Example Post #1 | Example Post #2 |
|--------|-------------------------|------------------------------|------------------------------|
| Media & Highlights | Direct video clips of gameplay or in-game events | Padres extend their lead to five with a Jackson Merrill towering 2-run shot in the 9th | The Rays take the lead and drop a 4-run 5th inning on Shohei Ohtani |
| News & Official | Direct links to reports, signings, transactions, or injury updates from recognized media or MLB sources | [MLBTR] Braves To Select Carlos Carrasco, Jair Camargo | [Stebbins] Out in Milwaukee, the Guardians recalled Kahlil Watson from Triple-A Columbus while placing Chase DeLauter on the 10-day injured list |
| Facts & Analysis | Structured arguments supported by specific, verifiable statistical evidence (e.g., WAR, ERA+, historical trends), including fun facts | Brett Kerry of the Angels just recorded a 5 pitch scoreless inning whilst also committing two errors | On this date in 1960, Ted Williams became the 4th member of the 500 HR club — here's what the leaderboard looked like on 6/17/1960 |
| Discussions & Opinions | Subjective discussions, opinions, or "hot takes" | Has anyone seen an mlb sculpture that is a good likeness of its subject? | Adjustments after breaking Hamate |

---

## Hard Edge Cases
<!-- What type of post will be genuinely ambiguous between two labels? How will you handle it when you encounter it during annotation? -->
| Labels | Definition of Label | Ambiguities / Edge Cases | Example Post | How to Handle It |
|--------|-------------------------|---------------------------|-------------------------|----------------------|
| Media & Highlights | Direct video clips of gameplay or in-game events | Clips paired with an analytical caption | [CloseCallSports] Explains the "Contreras Rule" in relation to José Caballero's pitch clock "antics" and warning given by ump in Sunday's game against the Blue Jays | If the video is the focus, use "Media & Highlights". If the text is the focus, use "Analysis". |
| News & Official | Direct links to reports, signings, transactions, or injury updates from recognized media or MLB sources | Historical facts presented as the news | The Red Sox are the 2nd time in MLB history since 1898 to leave 13+ runners on base and score 1 or 0 runs in back-to-back games, joining the 1919 Washington Nationals. | If it is a simple statement of an event, use "News & Official". If it interprets the event, use "Facts & Analysis". |
| Facts & Analysis | Structured arguments supported by specific, verifiable statistical evidence (e.g., WAR, ERA+, historical trends), including fun facts | Subjective opinions that mention a stat but don't use it to prove an argument | [TJStats] My Top 100 MLB Prospects | If a specific stat is used to support a logical claim, use "Facts & Analysis". If there is an image that includes statistical information, use "Facts & Analysis". If no stat or evidence is included, use "Discussions & Opinions". |
| Discussions & Opinions | Subjective discussions, opinions, or "hot takes" | Power rankings or speculative articles from sports media | NBC Sports MLB Power Rankings: Schlittler showing Cy Young form for Yankees, White Sox aren’t going away | If the post is an opinion piece (even if written by a journalist), use "Discussions & Opinions" as it represents an argument rather than a raw fact. |

---

## Data Collection Plan
<!-- Where will you collect examples? How many per label? What will you do if a label is underrepresented after 200 examples? -->
I will collect examples from r/baseball subreddit. It will have like 120 posts on "Media & Highlights", 50 posts on "News & Official", 20 posts on "Facts & Analysis", and 10 posts on "Discussions & Opinions". If a label is underrepresented after 200 examples, I will use a target search to fill the gaps, using the keywords such as "Opinion", "Discussion", "Prediction", or "Why do you think ..." to surface subjective discourse.

---

## Evaluation Metrics
<!-- Which metrics will you use to evaluate your model and why are those the right ones for this specific task? (Accuracy alone is not enough — explain what else you need and why.) -->
I will use accuracy, classification report, and confusion matrix to evaluate my model. These are the right ones for this specific task because accuracy can give a high-level view of overall performance, classification report can see if the model is failing to identify the rare "Discussion & Opinions" posts entirely, and confusion matrix can visualize where the model gets confused or what type of posts are misclassified. These can let me to make adjustments on "Hard Edge Cases" section to classify the posts correctly.

---

## Definition of Success
<!-- What performance would make this classifier genuinely useful? What would you accept as "good enough" for deployment in a real community tool? -->
I would make this classifier genuinely useful by "80% recall" goal for highlights and "90% precision" goal for "Facts & Analysis" label. There are many posts that can be classified as "Media & Highlights" since there is a scoreboard update or fine plays happening. For the "Facts & Analysis" label, if the user clicks the post, they should be able to see either written or image-posted statistical information about the facts. I would accept these two things as "good enough" for deployment in a real community tool because they prioritize user trust. For "Media & Highlights," high recall ensures the tool acts as a reliable archive—users won't miss the key moments of a game. For "Facts & Analysis," the 90% precision threshold is vital because these posts represent high-effort content. If a user filters for "Analysis" and is served low-effort "Discussions" instead, the tool loses credibility. Achieving these thresholds ensures that the tool is both comprehensive for casual fans (via highlights) and high-quality for power users (via analysis).

---

## AI Tool Plan
<!--- Add an AI Tool Plan section to your planning.md. This project's workflow is different from implementation projects — there's no code to generate, so your plan should cover the three places where AI tools actually help here:
- Label stress-testing: Give the AI your label definitions and edge case description, and ask it to generate 5–10 posts that sit at the boundary between two labels. If it produces posts you can't classify cleanly, your definitions need tightening — do that now, before you annotate 200 examples.
- Annotation assistance: Decide whether you'll use an LLM to pre-label a batch of examples before reviewing them yourself. If yes, note which tool you'll use and how you'll track which examples were pre-labeled (for disclosure in your AI usage section).
- Failure analysis: Plan to give your list of wrong predictions to an AI tool and ask it to identify patterns before you write up your evaluation. Note what you'll look for and how you'll verify the patterns yourself. --->

- **Label stress-testing:** I will give ChatGPT my label definitions and edge case description to generate 5-10 posts that sit at the boundary between two labels. I will change the label definitions or edge case description if the generated posts are hard to classify.
- **Annotation assistance:** I will use an LLM to pre-label a batch of 50 posts. I will use Gemini to do this and I will track which examples were pre-labeled by adding the "Model_Label" and "Human_Verified_Label" columns.
- **Failure analysis:** After evaluating the model, I will export the posts where the model and I disagreed. I will feed the list of "wrong predictions" into Claude and ask for common patterns that led to these misclassifications. Then, I will verify these patterns to see if they reveal a flaw in my labels.