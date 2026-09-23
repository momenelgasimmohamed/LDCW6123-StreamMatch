# StreamMatch

A small C++17 console application inspired by movie discovery on Netflix. This is an educational, rule-based program, not Netflix software or an AI recommender.

## Provenance
This initial implementation and documentation were prepared with ChatGPT assistance. The included Git history records actual assistant-environment development, not the six students' contributions. The group must understand, review, test and develop the project under its course's AI rules. Do not relabel these commits as student-authored work.

## Planned inputs and outputs
Input: age (0-120), genre (1-4), mood (1-3), available time (30-240 minutes).
Output: up to three eligible fictional titles, duration, illustrative minimum age, a deterministic preference score and an explanation.
Hard filters: age eligibility and runtime. Soft preferences: genre and mood.
All film titles, summaries, durations and age labels are invented test data; they are not a real Netflix catalogue or official classifications.

## Development stages
1. Document purpose, inputs, outputs and validation.
2. Implement the fictional catalogue and deterministic selection logic.
3. Add the interactive interface.
4. Add and execute automated tests.
5. Review edge cases and document reproducible evidence.
