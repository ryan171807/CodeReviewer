🚀 Automated Code Review System Using Ensemble of Large Language Models
This project implements an Automated Code Review System that uses an ensemble of Large Language Models (LLMs)—Qwen 14B, CodeBERT, and DistilBERT—to perform binary classification on whether a given code change requires human review.

By leveraging ensemble learning, the system enhances accuracy, robustness, and scalability across multiple programming languages. This tool aims to reduce manual code review effort and optimize the CI/CD pipeline.

🧠 Problem Statement
The goal is to build a system that classifies code changes as:

"Review Required"
"No Review Needed"
This helps software teams automatically triage code changes and prioritize human intervention only when necessary.

📦 Dataset
Source: Open-source dataset by Microsoft.
Training Set: 265,836 samples
Validation Set: 31,252 samples
Test Set: 31,252 samples
Covers diverse code modifications (bug fixes, documentation updates, function additions, etc.) across multiple languages.
⚙️ Methodology
Fine-Tuning of Individual Models:

Each LLM was fine-tuned on the Microsoft dataset to adapt to real-world code review scenarios.
Used the [CLS] token embedding for classification.
Applied a linear layer followed by softmax to output class probabilities.
Models Used:

CodeBERT: Strong performance across general-purpose languages.
DistilBERT: Better performance in structured languages like C++ and Ruby.
Qwen 14B: Performs well on straightforward and short patches.
Ensemble Strategy:

Combined predictions of all three models.
Focused on minimizing false negatives to avoid missing risky code changes.
Ensemble output is based on majority voting and consensus.
📊 Performance
Model	Accuracy	Precision	Recall	F1-Score
CodeBERT	83.55%	88.14%	93.29%	90.64%
DistilBERT	82.85%	88.50%	91.86%	90.15%
Qwen 2.5B	72.64%	88.10%	78.58%	83.07%
Ensemble	83.66%	87.90%	93.80%	90.70%
🔍 Key Insight: The ensemble model improves overall robustness and minimizes error rates, especially in short (0–250 tokens) and mid-length code patches.

🔬 Error Analysis
The ensemble model effectively reduces false negatives, even at the cost of slight increases in false positives.
It performs particularly well on critical code changes like bug fixes or new method additions.
Outperforms individual models in edge cases where simple logic or minimal changes are made.
🌍 Language Adaptability
Handles multi-language codebases effectively.
DistilBERT performs best in C++ and Ruby.
CodeBERT shows strong performance in Java, Python, and JavaScript.
Ensemble reduces variance caused by individual model weaknesses.
🛠️ Tech Stack
Python, PyTorch, HuggingFace Transformers
LLMs: CodeBERT, DistilBERT, Qwen 2.5B
Training: GPU-accelerated fine-tuning (Google Colab / local)
Evaluation: Sklearn, Matplotlib, Precision-Recall analysis
📈 Results Summary
✅ Binary classification output improves automation in CI/CD pipelines.
📉 Reduced manual review load by ~50% in testing simulations.
🔐 Safe predictions favored by prioritizing recall over precision in ensemble model.
🌐 Scalable to different projects and programming languages.
📌 Future Work
Extend to multi-label classification for categorizing code changes.
Integrate into GitHub Actions or similar CI/CD tools for real-time review feedback.
Add support for code diff visualization and model explainability (e.g., attention maps).
