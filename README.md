# bcog200-stroop-effect-experiment
**PROJECT DESCRIPTION**
This project implements an interactive Stroop Effect experiment using a graphical user interface (GUI) in Python. Users will be presented with color words displayed in different text colors and must identify the color of the text rather than the word itself. The program will measure reaction time and accuracy across trials and analyze differences between congruent and incongruent conditions. The goal is to demonstrate cognitive interference and provide users with a simple experimental psychology tool.

**WHY THIS PROJECT**
The Stroop Effect is a classic cognitive psychology phenomenon that demonstrates how automatic processes interfere with controlled processing. This program allows users to experience this effect firsthand while also generating measurable behavioral data.

**PLANNED FILE STRUCTURE**
- stroop_gui.py: Handles the GUI, experiment flow, and user interaction
- analysis.py: Processes and analyzes collected data
- tests/test_stroop.py: Contains unit tests for core functions

**PLANNED FUNCTIONS**
generate_trial(colors: list) -> dict

Generates a Stroop trial with a word, display color, and condition (congruent or incongruent).

run_experiment(num_trials: int) -> list

Runs the full experiment, records user responses, reaction times, and correctness for each trial.

analyze_results(results: list) -> dict

Calculates average reaction times and accuracy, separated by congruent and incongruent trials.

**EXAMPLE USE CASE**

A user launches the program and completes a series of Stroop trials through the GUI. After finishing, they receive feedback showing their reaction times and accuracy, as well as a comparison between congruent and incongruent performance.

**DATA STRUCTURE**

Each trial will be stored as a dictionary with the following format:

{
    "word": "RED",
    "color": "blue",
    "condition": "incongruent",
    "response": "blue",
    "correct": True,
    "reaction_time": 1.23
}

A list of these dictionaries will be used for analysis.

**TESTING PLAN**

The program will include unit tests to verify:

correct generation of Stroop trials
accurate classification of congruent vs incongruent trials
correctness of analysis calculations

**PYTHON SCRIPT FILES**


import random
import time
import tkinter as tk

COLORS = ["red", "blue", "green", "yellow"]


def generate_trial(colors):
    """Generate a Stroop trial."""
    word = random.choice(colors)
    color = random.choice(colors)

    condition = "congruent" if word == color else "incongruent"

    return {
        "word": word,
        "color": color,
        "condition": condition
    }


def run_experiment(num_trials):
    results = []

    for _ in range(num_trials):
        trial = generate_trial(COLORS)
        # GUI presentation will go here
        # record response + reaction time

        results.append(trial)

    return results



def analyze_results(results):

    congruent_times = []
    incongruent_times = []

    for trial in results:
        if trial["condition"] == "congruent":
            congruent_times.append(trial["reaction_time"])
        else:
            incongruent_times.append(trial["reaction_time"])

    return {
        "congruent_avg": sum(congruent_times) / len(congruent_times) if congruent_times else 0,
        "incongruent_avg": sum(incongruent_times) / len(incongruent_times) if incongruent_times else 0
    }


from stroop_gui import generate_trial

def test_generate_trial_structure():
    trial = generate_trial(["red", "blue"])

    assert "word" in trial
    assert "color" in trial
    assert "condition" in trial


def test_condition_logic():
    trial = generate_trial(["red"])
    assert trial["condition"] == "congruent"


def test_valid_values():
    trial = generate_trial(["red", "blue"])
    assert trial["word"] in ["red", "blue"]
    assert trial["color"] in ["red", "blue"]


    
