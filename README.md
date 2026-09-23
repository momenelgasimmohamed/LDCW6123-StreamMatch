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

## Build and run
You need a C++17 compiler. CMake is optional; Python 3 is only needed for the automated CLI tests.

### Direct compiler command (Linux, macOS, or Windows with g++)
```sh
g++ -std=c++17 -Wall -Wextra -Wpedantic src/main.cpp src/recommender.cpp -o streammatch
./streammatch
```
In Windows PowerShell use `g++ ... -o streammatch.exe` and `./streammatch.exe`.

### CMake (also supports Visual Studio on Windows)
```sh
cmake -S . -B build
cmake --build build --config Release
```
Run `./build/streammatch` on a single-configuration build. For a Visual Studio build, run `./build/Release/streammatch.exe`.

### Tests
```sh
ctest --test-dir build -C Release --output-on-failure
```
CMake runs both suites when Python 3 was found during configuration. To inspect details:
```sh
./build/unit_tests
python tests/test_cli.py ./build/streammatch
```
On Visual Studio builds use the executables under `build/Release/` instead. The current assistant-environment results are in `evidence/`. They are not a substitute for running the project on the group's own computers.

## Demo inputs
Menu `2`, age `23`, genre `2`, mood `1`, time `95` produces Campus Detour and Weekend Mix-Up with 8/8, followed by Robot Roommate with 3/8. A 30-minute limit produces no eligible title. Menu `0` exits.

## Code map
- `src/recommender.hpp`: data structures and function interfaces.
- `src/recommender.cpp`: fictional data, strict input parsing and deterministic ranking.
- `src/main.cpp`: repeated menu, prompts, explanations and clean EOF handling.
- `tests/test_recommender.cpp`: 33 named unit checks, including an 840-combination sweep.
- `tests/test_cli.py`: 18 black-box CLI cases.

## Explain the score
Five points for preferred genre, three for preferred mood. The weights are teaching design choices, not empirically validated Netflix weights. Age and runtime never contribute bonus points: they decide eligibility first. Ties use runtime, then unique ID. A title with 0/8 may appear only as a clearly labelled eligible alternative when stronger matches are unavailable.

## Continue development honestly
Clone the accompanying bundle to preserve provenance:
```sh
git clone ../streammatch_history.bundle streammatch-team
cd streammatch-team
git config user.name "YOUR REAL NAME"
git config user.email "YOUR OWN EMAIL"
git switch -c review/your-name
```
Check the relative bundle path from your own folder. Do real review or improvements, then commit only what you actually changed. Keep the initial assistant attribution intact. Record test results from your own machine. Do not backdate or invent member commits.

To export the required history after your group's work:
```sh
git log --oneline --graph --all --decorate
git log --date=iso-strict --format="%h | %an | %ad | %s" --all
```
The handout contains `--online`; the correct Git option is `--oneline`. See the official Git documentation: https://git-scm.com/docs/git-log

Upload only code, tests and non-sensitive documentation to a repository accessible to your tutor. Do not upload signatures, IDs or this report to a public repository. Set repository access yourself and paste the actual link into the report. No hosted repository has been created by this package.
