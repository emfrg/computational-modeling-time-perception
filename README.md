# Losing Track of Time

*Computational cognitive modeling of prospective timing under sequential multitasking.*

---

This repository contains the code, data, and analysis for the [MSc thesis](https://studenttheses.uu.nl/handle/20.500.12932/50349) by Emmanuel Fragkiadakis (Utrecht University, 2025). It includes a behavioral experiment (built with PsychoPy), a prototype cognitive model inspired by ACT-R (written in Python), the data used for the analysis and the analysis notebooks.

#### Code

- Behavioral experiment: `[/experiment](./experiment)`
- Cognitive model: `[/model](./model)`
- Data used in the study: `[/data](./data)`
- Statistical analysis & model fitting: `[/analysis](./analysis)`

## Experiment

The study uses a 2×2 within-subjects design crossing interruption condition (interrupted vs. sequential) with cognitive load (1-back vs. 2-back). Participants type words on an alphabetical virtual keyboard — the word disappears after the first letter, loading working memory — while a digit N-back task serves as the secondary task. In the interrupted condition the N-back interrupts the typing mid-word; in the sequential condition the two tasks are performed one after the other. After each trial participants give a verbal time estimate via a slider.

For details on the experimental design and stimuli see the [thesis](https://studenttheses.uu.nl/handle/20.500.12932/50349).

## Cognitive Model

The model is a prototype cognitive architecture for prospective timing under task interruptions. It integrates a reimplementation of the timing module by Taatgen et al. (2007) into the interruptions model of Borst et al. (2015), building on ACT-R's modular design and central production system (Anderson et al., 2004).

Key mechanisms:

- **Pacemaker–accumulator timing.** An independent pacemaker emits pulses into a temporal buffer. A `CheckBuffer` production reads and encodes them into a subjective duration.
- **Production competition.** Cognitive operations (typing, N-back matching, time checking) compete for a serial processing bottleneck. Under higher cognitive load, the timing production fires less often, causing pulses to be overwritten before encoding — leading to systematic underestimation.
- **Task switching costs.** Interruptions add reconfiguration overhead that further delays time-checking, amplifying underestimation beyond the effect of cognitive load alone.

For a full description see the [thesis](https://studenttheses.uu.nl/handle/20.500.12932/50349).

## Table of Contents

- [Getting Started](#getting-started)
- [Prerequisites](#prerequisites)
- [Environment Setup](#environment-setup)
- [Running Model Simulations](#running-model-simulations)
- [Running Experiment](#running-experiment)
- [Data Analysis](#data-analysis)
- [Support](#support)
- [Citation](#citation)

## Getting Started

### Clone the Repository

First, clone this repository to your local machine:

```bash
git clone https://github.com/emfrg/computational-modeling-time-perception.git
cd computational-modeling-time-perception
```

## Prerequisites

This project requires **Python 3.10** specifically to ensure compatibility with PsychoPy running from source and its dependencies.

### Installing Python 3.10

#### macOS

1. **Using Homebrew (recommended):**
  ```bash
   brew install python@3.10
  ```
2. **Using official installer:**
  - Download Python 3.10 from [python.org](https://www.python.org/downloads/release/python-31011/)
  - Run the installer package
  - Verify installation: `python3.10 --version`

#### Windows

1. Download Python 3.10 from [python.org](https://www.python.org/downloads/release/python-31011/)
2. Run the installer
  - **Important:** Check "Add Python 3.10 to PATH"
  - Select "Install Now" or customize as needed
3. Verify installation by opening Command Prompt: `python --version`

## Environment Setup

### Creating and Activating Virtual Environment

#### macOS

1. **Create virtual environment:**
  ```bash
   python3.10 -m venv .venv
  ```
2. **Activate virtual environment:**
  ```bash
   source .venv/bin/activate
  ```
3. **Install dependencies (excl. PsychoPy):**
  ```bash
   pip install -r requirements.txt
  ```

#### Windows

1. **Create virtual environment:**
  ```cmd
   python -m venv .venv
  ```
2. **Activate virtual environment:**
  ```cmd
   .venv\Scripts\activate
  ```
3. **Install dependencies (excl. PsychoPy):**
  ```cmd
   pip install -r requirements.txt
  ```

**Deactivate when done:**

```bash
deactivate
```

## Running Model Simulations

Ensure your virtual environment is activated before running simulations.

### Single Tasks (N-back, Typing)

```bash
python -m model.simulations.tasks
```

### Complete Experiment

```bash
python -m model.simulations.experiment
```

## Running Experiment

The behavioral experiment requires PsychoPy. Ensure you're using the Python 3.10 virtual environment we created before.
You can also choose to create a new virtual environment with Python 3.10 or run from the PsychoPy Builder.

### Installation and Execution

Assuming you are still inside the .venv virtual environment:

1. **Navigate to experiment directory:**
  ```bash
   cd experiment
  ```
2. **Install PsychoPy:**
  ```bash
   pip install psychopy
  ```
3. **Run the experiment:**
  ```bash
   python multitasking_experiment.py
  ```

*Note: The terminal or IDE may require input monitoring permission on macOS.*

### Alternative Method (if installation issues occur)

If you encounter problems with the command-line installation of PsychoPy:

1. Download PsychoPy Builder from [psychopy.org](https://www.psychopy.org)
2. Open PsychoPy Builder
3. Load the experiment script .py file
4. Run directly from the Builder interface

## Data Analysis


| Notebook                    | Description                                                                                                                                  | Colab                                                                                                                                               |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `experiment_analysis.ipynb` | Preprocessing, descriptive statistics, 2x2 RM-ANOVAs for task performance and time perception, scalar property and central tendency analyses | [Open In Colab](https://colab.research.google.com/github/emfrg/computational-modeling-time-perception/blob/main/analysis/experiment_analysis.ipynb) |
| `simulation_analysis.ipynb` | Single-task simulations, multitasking simulations, model fitting, 2x2 RM-ANOVAs on simulated data                                            | [Open In Colab](https://colab.research.google.com/github/emfrg/computational-modeling-time-perception/blob/main/analysis/simulation_analysis.ipynb) |


## Support

For issues or questions, please contact the researcher Emmanuel Fragkiadakis at [m.frgdakis@gmail.com](mailto:m.frgdakis@gmail.com)

## Citation

If you use this code or data in your research, please cite:

Fragkiadakis, E. (2025). *Losing track of time: Computational cognitive modeling of prospective timing under sequential multitasking* [Master’s thesis, Utrecht University]. Utrecht University Student Theses Repository. [https://studenttheses.uu.nl/handle/20.500.12932/50349](https://studenttheses.uu.nl/handle/20.500.12932/50349)

### BibTeX:

```bibtex
@mastersthesis{fragkiadakis2025losingtrack,
  title={Losing Track of Time: Computational Cognitive Modeling of Prospective Timing Under Sequential Multitasking},
  author={Fragkiadakis, Emmanuel},
  year={2025},
  school={Utrecht University},
  type={Master's thesis},
  url={https://studenttheses.uu.nl/handle/20.500.12932/50349},
  note={Code and data available at: \url{https://github.com/emfrg/computational-modeling-time-perception}}
}
```

