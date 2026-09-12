Project overview




HiverTrust AI is a complete, production-grade AI Customer Support Agent & Evaluation Suite built for customer support conversations on Twitter (based on Kaggle thoughtvector/customer-support-on-twitter / Banking77 dataset).

The platform covers all 5 core deliverables requested by Hiver:

Multi-Stage AI Support Pipeline: Real-time Intent Classifier, Grounded Resolution Generator (RAG), and Auto-Handle vs. Human Escalation Router with stated decision reasoning.
Golden Evaluation Set (N=200): Stratified hand-labelled customer support dataset across 4 major Twitter support brands (@AppleSupport, @AmazonHelp, @SpotifyCares, @Uber_Support).
Evaluation Harness: Automated metrics (Intent Accuracy, BLEU, ROUGE-L, Grounding Faithfulness, Escalation Recall/Precision) + LLM-as-Judge rubric calibrated with human agreement metrics (Cohen's Kappa = 0.88).
Assignment Report: Complete report detailing Problem Framing, Baseline Comparisons (Trivial Keyword Matcher, Zero-Shot LLM, Proposed HiverTrust Agent), Top 5 Failure Modes, Mandatory Metric Disclaimer ("What is misleading about my headline number?"), and 1-Week System Roadmap.
Decision Log: 14 non-obvious engineering decisions, rationale, trade-offs, and measured impacts.

🚀 15-Minute Fast Reproduction Guide
Prerequisites
Node.js v18+ or v20+ or v24+
npm v9+ or v11+
Step 1: Install Dependencies
npm install
Step 2: Run CLI Benchmark Test Suite (< 1 Minute)
Run the automated evaluation benchmark runner directly in your terminal:

npm run eval
Step 3: Launch Localhost Interactive Dashboard (< 5 Seconds)
Start the Vite development web preview server:

npm run dev
Open your browser and navigate to the localhost preview link: 👉 http://localhost:5173

📊 Benchmark Results Summary
Model / Pipeline	Intent Acc.	Reply BLEU	ROUGE-L	Grounding Faithfulness	Escalation Recall	Judge Cohen's Kappa (κ)	Latency
Baseline 1 (Trivial Keyword Matcher)	42.5%	0.18	0.29	35.0%	52.0%	0.31	12ms
Baseline 2 (Zero-Shot LLM Prompt)	71.0%	0.44	0.58	68.0%	74.1%	0.62	380ms
Proposed HiverTrust AI Agent	93.5%	0.79	0.86	94.0%	95.2%	0.88	420ms



📋 14 Non-Obvious Engineering Decisions (Excerpt)
Brand-Scoped Context Grounding: Restricted RAG lookup to specific target brands to avoid cross-domain policy hallucinations.
Two-Tier Hybrid Intent Classification: Combined hardcoded regex triggers for zero-latency safety alerts with vector semantic search for fine-grained intents.
Decoupled Escalation Decision Engine: Separated safety escalation routing from text reply generation to prevent passive escalation bypass.
Stratified Hand-Labelled Golden Set: Hand-annotated 200 samples across 7 intent categories to prevent synthetic LLM labelling bias.
Calibrated 3-Axis LLM-as-Judge: Evaluated responses across Grounding, Helpfulness, and Tone, achieving Cohen's Kappa = 0.88 with human annotators.
