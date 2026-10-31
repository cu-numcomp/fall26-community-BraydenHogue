# Community Software Analysis Proposal
Please edit this file and push to your repository.

## Software: scikit-learn

scikit-learn is a machine learning library for Python, though that's not specifically why I picked it. It covers classification, regression, clustering, dimensionality reduction, and anomaly detection, all built on NumPy and SciPy. Its primary audience is data scientists, researchers, students, and engineers who need access to general purpose machine learning tools. Because the library is so large, I'm focusing on its anomaly detection tools, specifically `IsolationForest` and `EllipticEnvelope`, and how they perform on actual network traffic. This will be a continuation of my exploration 1 in the sense that I'm attempting to detect attacks hidden in network traffic, this time using a widely used library alongside real network traffic data.
 
I'm interested in it because it gives me further opportunity to link what I'm learning in numerical computation to cybersecurity since anomaly detection on network traffic puts concepts such as conditioning, how forming AᵀA squares the condition number, the SVD, and the bias-variance tradeoff into practice. scikit-learn can download the KDD Cup 1999 intrusion detection dataset directly with `fetch_kddcup99`, including an HTTP subset of real network connections labeled as normal or attack, so I can test whether these detectors actually catch attacks and see where the numerical issues start affecting the results.

### Stats

| Description | Your answer |
|---------|-----------|
| Repository URL |https://github.com/scikit-learn/scikit-learn|
| Main/documentation website |https://scikit-learn.org|
| Year project was started |2007, as a Google Summer of Code project (git history begins January 2010)|
| Number of contributors in the past year |198|
| Number of contributors in the lifetime of the project |About 3,500 (3,658 name and email entries from `git shortlog -se`, 3,478 distinct names)|
| Number of distinct affiliations |>10|
| Where do development discussions take place? |GitHub issues and pull requests, plus GitHub Discussions, Discord, and a mailing list|
| Typical number of emails/comments per week? |About 50 new issues and pull requests opened per week|
| Typical number of commits per week? |About 19|
| Typical commit size |Median of 2 files and 29 lines changed per commit|
| How does the project accept contributions? |pull requests|
| Does the project have an automated test suite? |yes|
| Does the project use continuous integration? |yes|
| Does the project have an AI contribution policy? |https://scikit-learn.org/stable/developers/contributing.html#automated-contributions-policy|
| Are any legal/licensing steps required to contribute? |no|

### Install and run

Check the following boxes when complete or add a note below if you
encountered a problem.

- [x] I have installed the software
- [x] I have run at least one example
- [x] I have run the test suite
- [x] The test suite passes

### Notes/concerns/risks

scikit-learn an incredibly large library, so I'm limiting my analysis to its anomaly detection tools instead of the whole library.
 
The KDD99 dataset is dated and is built from simulated traffic, so results on it may be unrealistically good.

When I ran `EllipticEnvelope` on the KDD99 HTTP subset, it produced thousands of warnings that the determinant increased during a step that should only decrease it. The final results still looked good, but I want to investigate this further to find the root cause.

#### Note on copyright
Students retain copyright on any work done in completion of a CU
course, so you are authorized to sign a [contributor license
agreement (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement),
affirm a [developer's certificate of
origin (DCO)](https://en.wikipedia.org/wiki/Developer_Certificate_of_Origin),
etc.  If you have concerns about this, please note them and/or reach
out to Jed directly.
