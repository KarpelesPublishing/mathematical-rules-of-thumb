# Mathematical Rules of Thumb: companion notebooks and skills

Companion material for *Mathematical Rules of Thumb* by Jason Karpeles. Each chapter has a
Jupyter notebook that reproduces its calculations and figures, and a skill
that an AI assistant can use to teach the chapter.

Interactive version: https://karpeles.com/companions/mathematical-rules-of-thumb/
About the book: https://karpeles.com/publishing/mathematical-rules-of-thumb

## What is here

- `notebooks/`: one notebook per chapter, already run, so the results show on GitHub.
- `skills/`: a master skill for the book and one skill per chapter.

## Run the notebooks

You need Python 3.10 or later.

    pip install -r requirements.txt
    jupyter lab

Open any notebook in `notebooks/` and choose Run All.

## Use the skills

Each folder in `skills/` holds a `SKILL.md` file. To use one with Claude Code, copy the folder into `~/.claude/skills/` (or into your agent's skills folder):

    cp -r skills/mathematical-rules-of-thumb ~/.claude/skills/
    cp -r skills/13-statistics ~/.claude/skills/

The [master skill](skills/mathematical-rules-of-thumb/SKILL.md) routes a question to the right chapter. Each chapter skill lists the chapter's numbered rules with their conditions, explains how to apply them to your own inputs, and points to that chapter's notebook.

## Copyright

Copyright Jason Karpeles. All rights reserved.
