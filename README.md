# bcog200-stroop-effect-experiment
**PROJECT DESCRIPTION**
This project implements a simple version of the Stroop Effect experiment using Python. In the experiment, users will be shown color words (such as "RED" or "BLUE") displayed in different colored text. The participant must identify the color of the text rather than the word itself. The program will measure reaction time and accuracy to demonstrate the cognitive interference effect known as the Stroop Effect.

**PLANNED FUNCTIONS**
**generate_trial()**

This function will randomly generate a Stroop stimulus by selecting a color word and a display color. It will determine whether the trial is congruent (word and color match) or incongruent (word and color differ).

**run_trial()**

This function will present the stimulus to the user, collect their response, and measure their reaction time. It will return the response time and whether the response was correct.

**analyze_results()**

This function will take the results from multiple trials and calculate summary statistics such as average reaction time and accuracy. It will also compare performance between congruent and incongruent trials.
