# Agentic AI-Based Phishing Email Detection and Explanation System

A Google Colab student project combining a TF-IDF + Logistic Regression text classifier with four specialist agents: email analysis, threat detection, evidence explanation, and security recommendations. An optional CrewAI + Gemini section demonstrates LLM-powered sequential collaboration when an API key is configured.

## Files
- `Agentic_AI_Phishing_Email_Detection.ipynb` — main project notebook.

## Run it
1. Open Google Colab and upload/open the `.ipynb` notebook.
2. Run the cells from top to bottom.
3. Allow the public Hugging Face dataset to load.
4. Review the held-out evaluation metrics and confusion matrix.
5. Run the Gradio UI cell to test sample emails.
6. To enable the CrewAI review, add a Colab Secret named `GEMINI_API_KEY` and enable notebook access. In VS Code/Jupyter, set `GEMINI_API_KEY` in the kernel environment before launching the notebook (for example, in PowerShell: `$env:GEMINI_API_KEY = "your-key"`). Never paste the key into a notebook cell or commit it. The notebook defaults to `gemini/gemini-2.5-flash`; set `CREWAI_MODEL` to override it. Do not paste private email content into an LLM demo.

## Main technologies
Python, Hugging Face Datasets, pandas, scikit-learn, TF-IDF, Logistic Regression, CrewAI, Gemini API (optional), and Gradio.

## Important limitations
The dataset's labels are an imperfect proxy for real-world phishing. The model score is not a calibrated probability, and “Likely safe” is not a guarantee. The system does not open URLs, inspect attachments, or query live reputation services. It is an educational prototype, not a production security control.

## References
- Dataset: https://huggingface.co/datasets/zefang-liu/phishing-email-dataset
- CrewAI agents: https://docs.crewai.com/core-concepts/Agents
- Gemini + CrewAI: https://ai.google.dev/gemini-api/docs/crewai-example
