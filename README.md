<h1 align='center'> CSC Hackathon 2021, Prediction of email opening </h1>
<h3 align='center'> (not) a dream team </h3>
<table align="center">
  <tr>
    <td align="center">Andrii Yerko</td>
    <td align="center">Oleksandr Bratus</td>
  </tr>
    <tr>
    <td align="center">Artem Dikhtiar</td>
    <td align="center">Volodymyr Kuzko</td>
  </tr>
</table>


## "Conservative solution": Logistic Regression + analytical skills :)
[![nbviewer](https://img.shields.io/badge/nbviewer-EDA%20notebook-orange)](https://nbviewer.jupyter.org/github/andrii0yerko/CSC-Hackathon-2021/blob/main/emails-eda.ipynb) [![nbviewer](https://img.shields.io/badge/nbviewer-Submission%20notebook-green)](https://nbviewer.jupyter.org/github/andrii0yerko/CSC-Hackathon-2021/blob/main/final-solution-feature-engineering-log-reg.ipynb)

We started with EDA:
<p align='center'>
<img src=./images/eda.png/>
</p>
Based on EDA we created the following features, and trained the LogisticRegression on them:

- **MailBoxID** -> One Hot (29 uniques)
> - **ContactID** -> _dropped_ \
> (This is where we went wrong. According to the results of other teams, it was the most useful column)
- **TimeZone** column -> _TimeZone_, Region
- **TimeZone, SentOn** -> Recipient Hour (Sent time + TimeZone) 
  - Recipient Hour  -> DayTime features (Morning, Day, Evening, Night)
- **Subject** -> 
  - Length
  - IsResponse (1 if starts with RE:)
  - Stemming + Bag Of Words, ngrams=(1, 2), num_features=15000

-> feature selection -> LogisticRegression

---

### Embeddings? word2vec? BERT?
<p align='center'>
<img src=./images/clouds.jpg align='center'/>
</p>
We tried to use them instead of BoW, but they din't give any improvement, only worsened the result.

---

### Achieved 6th place out of 12:

|F1 on public LB| F1 on private LB |
|:----|-----|
|0.54618|0.54293|


<!-- <p align='center'> -->
<img src=./images/meme.jpg align='center'/>
<!-- </p> -->
