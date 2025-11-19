# CSB - Computational Systems Biology course at Universitat de València

This repository is the landing page for the Computational Systems Biology (CSB) course of the Universitat de València. It aggregates the hands-on materials for the three course sessions as git submodules so this repo serves as a single point of entry for students and instructors.

Each session is maintained in its own subdirectory and kept as a submodule to preserve history and allow independent development. The three sessions included here are:

- `session8/` — Constraint-based analyses and Boolean model simulations using the CoLoMoTo toolchain (GINsim, bioLQM, MaBoSS).
- `session9/` — PROFILE-oriented analyses combining shell, Python and R workflows; data processing and sample-specific model personalization.
- `session10/` — Constraint-Based Metabolic (CBM) modelling using COBRApy and the iJO1366 genome-scale *E. coli* model.

**This README** explains the repo purpose, how to clone and work with the submodules, and gives a short summary for each session. For detailed instructions and full exercises, open the README inside each `sessionN/` folder.

**Repository Structure**

- `session8/` — Practical notebook, example models and setup for Boolean modelling (CoLoMoTo).
- `session9/` — Scripts, PROFILE data and instructions combining shell, Python and R analyses.
- `session10/` — CBM tutorial, data and models for COBRApy-based exercises.
- `LICENSE`, `README.md` — This file and licensing information.

**Cloning this repository (with submodules)**

The recommended way to clone this repo and automatically initialize the session submodules is:

```pwsh
# Clone repository and init submodules in one step
git clone --recurse-submodules https://github.com/ArnauMontagud/CSB_course_UV

# Or, if you already cloned without submodules:
git submodule update --init --recursive
```


**Updating submodules**

To pull the latest changes for the main repo and its submodules:

```pwsh
git pull --rebase
git submodule update --init --recursive --remote
```

Or update a single session submodule manually:

```pwsh
cd session9
git checkout main
git pull
cd ..
```

Note: some submodules may use different branch names — check the submodule's README for details.

**Session summaries (brief)**

- `session8/` — Boolean modelling with CoLoMoTo

	The session focuses on Boolean and logical modelling workflows using GINsim, `bioLQM` and `MaBoSS`. The included notebook `CSB2025_practica.ipynb` demonstrates loading `.zginml` models (e.g., a Metastasis master model and a Prior Knowledge Network), computing stable states, converting models between tools, and running stochastic MaBoSS simulations (wild-type and mutants). The folder contains model files, setup instructions and small tasks to explore attractors, simulate mutants and compare with literature.

- `session9/` — PROFILE analyses: data processing and personalised models

	This session covers practical pipelines that combine shell scripting, Python and R to process biological datasets and produce sample-specific model inputs. Materials include `additional_files/` with PROFILE data and scripts, setup notes to prepare Python and R environments, and exercises to obtain GDSC cell line profiles, personalise PKN models and run MaBoSS simulations per cell line. The README inside `session9/` contains detailed data download and environment setup guidance.

- `session10/` — Constraint-Based Metabolic Modelling (CBM)

	This session is a hands-on tutorial on COBRA-based metabolic modelling using `COBRApy`. The `CBM_tutorial.ipynb` walks through toy model construction, loading the iJO1366 genome-scale model, performing flux balance analysis (FBA), single-gene knockout studies, comparison with in vivo essentiality datasets, and metabolic engineering design tasks. Data and models (e.g., `iJO1366.xml`, experimental lethals and media definitions) are provided under `session10/data/`.

**Requirements & recommended environments**

Each session provides its own `Setting-up.txt`, `INSTALL` or `requirements.txt` files describing the tools and packages required. Common recommendations:

- Use a `conda` environment named (for example) `CSB2025` to manage Python dependencies.
- Alternatively for CoLoMoTo/GINsim tasks, consider using the CoLoMoTo Docker image for reproducibility.
- For CBM tasks, install `cobra` and a linear-programming solver (`swiglpk`, or other supported solvers).

Check each `sessionN/README.md` for exact dependency versions and example commands.

**How to use this repository for teaching or self-study**

1. Clone the repository with submodules (see commands above).
2. Read the `README.md` inside the session folder you plan to work on (e.g., `session10/README.md`).
3. Set up the environment described in that session's setup file.
4. Open the main notebook (e.g., `CBM_tutorial.ipynb`, `CSB2025_practica.ipynb`) in VS Code or Jupyter and run cells top-to-bottom.

**Contributing / Updating session content**

- Session content is intentionally kept modular: if you want to update a session, enter the `sessionN/` folder, work on that submodule's repo, commit and push there. Then update the submodule reference in this top-level repo and push.
- Example: to update `session8` content locally, `cd session8`, make changes, push to the remote for that submodule, then from the top-level repo run `git add session8 && git commit -m "Update session8 submodule" && git push`.

**Authorship by session**

- `session8/`:
	- Authors include Vincent Noël, Aurélien Naldi, Laurence Calzone, Loïc Paulevé, and Denis Thieffry (see `session8/README.md` for citations).

- `session9/`:
	- Authors include Pauline Traynard, Jonas Béal and Arnau Montagud (see `session9/README.md` for citations).

- `session10/`:
	- Authors include Miguel Ponce de León and Arnau Montagud (see `session10/README.md`).

**License**

Materials are owned by each of the authors, the repositories are released under the BSD 3-Clause License. See the `LICENSE` file for details.

**Contact / Support**

If you find issues or need help, open an issue in this repository or contact the course instructor.
