# Program design

## Main menu
1. Browse the fictional catalogue
2. Recommend a movie
3. Explain how matching works
0. Exit

## Algorithm
Reject a movie when its minimum age exceeds the entered age or its duration exceeds available time. Among eligible movies, give five points for matching the selected genre and three points for matching the selected mood. Sort by score descending, then duration ascending, then unique ID ascending. Return up to three. The score is a preference score out of eight, not a probability or quality rating.

## Why this fits Part 1
The lifecycle study examines access to home entertainment. This program makes a small catalogue easier to navigate by matching viewing constraints and preferences. It illustrates discovery, not streaming delivery or market disruption.

## Validation
Only a complete integer, optionally surrounded by whitespace, is accepted. Reject blank input, decimals, trailing text, out-of-range values and overflow. End-of-file terminates cleanly. No personal information is saved or transmitted.
