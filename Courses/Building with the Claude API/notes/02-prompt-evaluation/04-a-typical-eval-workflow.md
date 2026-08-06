# A Typical Eval Workflow

A 6-step iterative process for improving prompts.

## Step 1 — Write an Initial Draft
Create a baseline prompt to optimize.

## Step 2 — Create an Evaluation Dataset
A collection of test inputs — can be 3 examples or thousands, hand-written or LLM-generated.

## Step 3 — Generate Prompt Variations
Interpolate each dataset input into the prompt template.

## Step 4 — Get LLM Responses
Feed each prompt variation to Claude and collect the outputs.

## Step 5 — Grade Responses
Use a grader system to score each response (e.g., on a 1–10 scale), then average the scores for overall prompt performance.

## Step 6 — Iterate
Modify the prompt based on the scores, repeat the entire process, and compare versions.

## Key Points

- There's no single standard methodology
- Many open-source and paid tools are available
- You can start simple with a custom implementation
- Grading complexity varies widely
- Objective scoring enables systematic, A/B-style prompt improvement
