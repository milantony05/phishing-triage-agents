# Project Report
## Agentic AI-Based Phishing Email Detection and Explanation System

**Student name:** [Enter name]  
**Course / subject:** Agentic AI  
**Platform:** Google Colab  
**Date:** [Enter date]

## 1. Abstract
This project implements an educational email-security assistant combining a TF-IDF + Logistic Regression classifier with a four-agent workflow for email analysis, threat detection, evidence explanation, and security recommendations. An optional CrewAI + Gemini layer provides an additional natural-language review. The system is evaluated on a held-out subset of a public labelled email dataset.

## 2. Problem Statement
Email-based social engineering is a common route for credential theft and fraud. Users may struggle to identify urgency, credential requests, suspicious links, and other warning signs. This project aims to provide a concise initial triage and explain the signals behind its assessment.

## 3. Objectives
- Build a supervised text classifier for safe versus phishing-labelled emails.
- Extract explainable indicators from supplied email text and URLs without opening links.
- Coordinate specialist agents to create an evidence-based result and recommend safe actions.
- Evaluate classification with accuracy, precision, recall, F1-score, ROC-AUC, and a confusion matrix.
- Demonstrate the workflow through a Gradio interface in Google Colab.

## 4. Tools and Technologies
Python, Google Colab, Hugging Face Datasets, pandas, NumPy, scikit-learn, TF-IDF, Logistic Regression, CrewAI, Gemini API (optional), and Gradio.

## 5. Dataset
Dataset: [zefang-liu/phishing-email-dataset](https://huggingface.co/datasets/zefang-liu/phishing-email-dataset). The notebook uses the `Email Text` and `Email Type` columns, maps `Safe Email` to 0 and `Phishing Email` to 1, removes empty and duplicate records, truncates long messages to 10,000 characters, and uses a stratified train/test split. State the final row counts observed in the notebook.

**Dataset limitation:** These categories are imperfect proxies for real-world phishing. Some examples may resemble broad unsolicited or spam-like email, and results may not generalize to current enterprise threats.

## 6. System Architecture
1. **Email Analysis Agent:** extracts URLs, sender details, urgency language, credential requests, and prize/payment lures.
2. **Threat Detection Agent:** scores the email using the trained TF-IDF + Logistic Regression pipeline and assigns a transparent triage level.
3. **Evidence and Explanation Agent:** displays rule-based indicators and influential model terms, then summarizes uncertainty.
4. **Security Recommendation Agent:** suggests cautious, defensive next steps based on the triage level.
5. **Optional CrewAI crew:** four sequential LLM agents produce a second explanation and recommendations; the CrewAI output does not replace the classifier label.

## 7. Methodology
- Data cleaning: missing values, empty messages, duplicates, label mapping, and text truncation.
- Feature extraction: TF-IDF word unigrams and bigrams.
- Classifier: Logistic Regression with class weighting.
- Evaluation: held-out stratified test set.
- Agent orchestration: structured outputs flow from analysis to detection to explanation to recommendation.

## 8. Results
Fill this table with the actual metrics from the notebook after it has run. Do not estimate values.

| Metric | Observed value |
|---|---:|
| Accuracy | [Fill from output] |
| Precision (phishing) | [Fill from output] |
| Recall (phishing) | [Fill from output] |
| F1-score (phishing) | [Fill from output] |
| ROC-AUC | [Fill from output] |

Insert the confusion-matrix screenshot and describe the false positives and false negatives observed.

## 9. Demonstration
Include screenshots from the Gradio interface for (a) a synthetic suspicious message and (b) a routine message. For each, report the classification, model score, risk level, evidence, and recommended actions. Do not present fabricated or manually chosen scores as model results.

## 10. Limitations and Responsible Use
- The score is not a calibrated probability.
- “Likely safe” does not guarantee safety.
- The dataset has label noise and may have temporal/domain shift.
- The prototype does not query live URL reputation, inspect attachments, authenticate senders, or connect to a mail server.
- The optional LLM flow transmits email text to the selected provider; only public or synthetic test messages should be used.
- The system is an educational prototype and must not be used as the sole basis for security decisions.

## 11. Future Enhancements
Use additional verified phishing corpora, calibrate scores, perform domain and sender authentication checks, add safe URL-reputation integrations, evaluate on a temporally separate dataset, support multiple languages, and conduct adversarial robustness tests.

## 12. Conclusion
Summarize what the system successfully demonstrates, quote the actual measured results, discuss the strengths of evidence-based multi-agent triage, and state the limitations that remain.

## References
- Dataset: https://huggingface.co/datasets/zefang-liu/phishing-email-dataset
- CrewAI agent concepts: https://docs.crewai.com/core-concepts/Agents
- Gemini + CrewAI example: https://ai.google.dev/gemini-api/docs/crewai-example
- TF-IDF: https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html
- Logistic Regression: https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html
