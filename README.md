# extractive-text-summarization

## Introduction
There is a virtually infinite amount of text-based data that currently exists; so much data is being generated that an individual could not possibly hope to consume it all. This text-based data is also uniquely useful to data analysts - from digesting consumer reviews on products and venues, gleaning key facts and locations from breaking news articles, to understanding what is popular and trending in an ever-changing internet landscape through social media posts. This creates an interesting point of tension: we want to use this data, but how do we access it? An effecitve and computationally inexpensive way is summarization!

## Summarization Techniques
There are two main summarization "umbrellas" that techniques fall under: Abstractive and Extractive summarization. There is some nuance to the way these different summarization styles operate, but in general:
Abstractive Summarization: Algorithmically selects sentences that are concise and semantically related, and glues them together to generate a summary.
Extractive Summarization: Algorithmically identifies the most informative sentences in a body of text, and glues them together to generate a summary.
In practice, Abstractive summarization is significantly more computationally expensive - though it gives you summaries a bit closer to what a human might create. Extractive summarization, conversely, is very lightweight and easy-to-implement but it entirely disregards semantics so the summaries you create may not make much sense. I will focus on Extractive summarization for the purposes of this project, because I am limited by the computational resources available to me.

## The Data
Articles I used to plug into my summary were sourced from this news articles database found [here](https://drive.google.com/file/d/1lhVi_4qc9Ei3p2WDqkkvtaQvqXnROi-G/view?usp=sharing). I selected 3 different articles to generate summaries, with differing topics - Television, Sports, and Lifestyle. The articles were intentionally selected to be difficult for my summarizers to manage - the TV article is long and full of flowery prose, the Sports article is comparing two different sports and topics throughout, and the Lifestyle article is a bullet-point style short piece.

## Summarization Techniques
The Extractive summarization pipeline can be reduced to 3 important steps: 1) splitting the document into sentences, 2) comparing similarity between those sentences, and 3) ranking sentences and returning them in ranked order. The main point of difference between Extractive summarization techniques is on step 2 - determining similiarity between sentences. In this project, I will utilize 5 different summarization techniques, each with their own way of determining similarity. Those techniques are:
* Cosine Distance
* Tfidf
* PyTextRank
* GenSim
* LexRank

## Results
Effectiveness of the summarizers was measured both qualitatively and quantitatively. The qualitative approach takes a look at each summary generated and evaluates it based on its semantical construction - put simply: does this summary make any sense?
### The Good!
| Summarization Technique | Summary |
| --- | --- |
| LexRank | Dishwasher Clean your dishwasher monthly to prevent a buildup of germs and maintain the efficiency of the machine — you want to make sure your dishes are clean! Afterward, leave your dishwasher open for a few hours to air it out. When you wash items in hot water, your machine is being cleaned as well, but once a month, you should still run an empty load with hot water and about a cup of distilled white vinegar to sanitize the basin and wipe out any lingering germs. |
### The Not-So-Good
| Summarization Technique | Summary |
| --- | --- |
| Tfidf | “Obviously I want to play well and see how I handle tournament golf,” Curry said.  “I’m honoured to have the opportunity to play with the pros,” Curry said.  “I’ve had great times in my cricket career but at this stage golf is No1,” he said.  “I always say cricket was my job and golf is my passion.  One also presumes Curry has plenty of means by which he can assist said foundation.|

The quantitative approach utilizes n-grams compared to a human-generated summary (I created summaries of my own for each article). While I am by no means an expert summarizer, the idea is that if a computer-generated summary is closer in structure and meaning to the human-generated one it receives a higher score and is, overall, a better summary.

Summarization Technique | TV | Sports | Life | Mean
--- | --- | --- | --- | ---
Cosine | 0.189 | 0.178 | 0.147 | 0.171
Tfidf | 0.247 | 0.060 | 0.217 | 0.175
PyTextRank | 0.220 | 0.217 | 0.144 | 0.194
GenSim | 0.211 | 0.178 | 0.202 | 0.197
LexRank | 0.242 | 0.167 | 0.252 | 0.220

## Future Goals
* Refine summarizers to create better summaries
* Retool the cleaning step of the pipeline to allow for more types of articles (e.g. different langues, handles more encodings, etc.)
* Build an Abstractive Summarizer!
