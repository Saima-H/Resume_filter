# Resume_filter
A workflow proposed to filter resumes , in order to select the best candidates to be interviewed.
Proposed by :Saima Muzaffar Hussain(M.E CSE) & Atifa Raheel(M.E CS)

Proposed workflow:
<img width="1250" height="1125" alt="image" src="https://github.com/user-attachments/assets/466c644c-5a9e-4e10-870d-b4d1369e9eb8" />

This project automates the transition from unstructured resume text to a definitive hiring verdict. It uses a three-phase pipeline to quantify candidate potential through Geometric Mean Scoring and Rule-Based Arbitration.
The Three-Phase Architecture
Phase 1: Intelligent Data Ingestion (The Extraction)

Process: Converts raw PDF text into a structured JSON dataset.

Normalization: The AI extracts and scores four core metrics on a scale of 0.0 to 1.0:

S (Skills): Technical proficiency.

T (Trajectory): Career growth and velocity.

I (Impact): Measurable achievements and leadership.

R (Relevance): Alignment with the specific industry or role.

Persistence: Parsed data is stored in a SQLite database to eliminate redundant API costs and enable high-speed lookups.
Phase 2: Weighted Mathematical Scoring (The Filter)Geometric Mean Formula: Applies role-specific exponents (a, b, c, d) based on the persona (Junior, Executive, or Specialist):
<img width="922" height="262" alt="image" src="https://github.com/user-attachments/assets/fb2ac8ff-5f10-4b88-8c24-4bef2854ccfc" />
Phase 3: Compensatory Brain (The Logic)Logic:
A rule-based engine resolves ambiguity by identifying specific candidate strengths that math might miss:
Rule A (Transferable Expert): High Skills (S) compensate for low Relevance (R).
Rule B (High Potential): Top-tier Trajectory (T) compensates for low total Experience (exp\_years).
Rule C (Stagnant Specialist): Low Trajectory/Impact (T or I) negates high Skills/Tenure.

Key Technical Features
Multi-Persona Support: Dynamic weighting shifts (e.g., Executive roles prioritize Impact, while Junior roles prioritize Skills).

Database-Driven Workflow: Uses SQLite for data persistence, allowing for instant re-evaluations for different roles without re-parsing PDFs.

Resilient Design: Built-in error handling with exponential backoff to manage LLM API rate limits.

Anti-Cheating Logic: Because it uses a Geometric Mean, a "zero" in any core category (like a total lack of skills) cannot be hidden by a high score in another—the whole score collapses to zero.



