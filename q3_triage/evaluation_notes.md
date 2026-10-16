\# Q3 ESG Message Triage Evaluation



\## Setup

Tested on 16 October 2026 using Ollama and llama3.2:1b.

Three messages were processed twice with temperature 0 and seed 42.

A keyword-based baseline compared category, urgency, follow-up and team.



\## Prompt

The original prompt lacked category definitions, urgency criteria and

routing rules. The revised prompt added these, confidentiality guidance,

uncertainty preservation and instructions against inventing information.

Only the revised prompt was tested.



\## Results

\- M1: Correct category, urgency and team, but incorrectly stated that

&#x20; recycling contamination required no follow-up.

\- M2: Classified an electrical water hazard as MEDIUM rather than CRITICAL,

&#x20; selected Facilities instead of Emergency Response, omitted the electrical

&#x20; hazard from the summary and incorrectly rejected follow-up.

\- M3: Misclassified supplier misconduct as WASTE and returned WASTE as an

&#x20; invalid team. Sensitivity changed from MEDIUM to LOW between repeats,

&#x20; although the prompt required HIGH for confidential allegations.



All six responses were parseable JSON; four passed schema validation.

M1 and M2 outputs were identical across repeats. M3 failed validation,

so automated consistency assessment was skipped; manual review identified

differences in sensitivity and summary wording.



\## Baseline and Limitations

The baseline matched all four expected fields for all three messages.

However, these selected examples suit its keyword rules and do not prove

general superiority. Three distinct messages cannot establish production

accuracy or demographic fairness. Repeated errors demonstrate that

consistency and schema validity do not guarantee correct decisions.



\## Recommendation

The current configuration is unsuitable for autonomous routing.

Require human review, validate team/category consistency and check

follow-up contradictions. Test clearer examples, stronger models and

broader inputs before considering a supervised pilot. Minimise personal

data and restrict access to confidential messages and logs.



\## Evidence

See comparison.csv, experiment\_log.json, consistency.json,

messages\_and\_expected.json, saved prompts and screenshots S1–S5.

