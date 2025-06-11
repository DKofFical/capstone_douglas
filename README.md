Welcome to this project. Here are a few instructions.

**About the research**
Abstract: Large language models (LLMs) are increasingly integrated into human-facing applications, making it critical to evaluate their social reasoning capabilities, particularly their ability to understand and predict human mental states—a core aspect of the Theory of Mind (ToM). While existing benchmarks demonstrate that LLMs can achieve near-human performance in static, isolated scenarios, they fall short of capturing the dynamic nature of real-world belief formation, where human beliefs evolve in response to perceptual experiences. To address this gap, we introduce BC-ToM, a novel evaluation framework designed to assess LLMs’ ability to detect and identify belief changes triggered by multi-sensory perceptual cues. The benchmark evaluates LLMs through three tasks: (1) detecting belief changes, (2) identifying updated beliefs, and predicting belief changes in noisy settings with distractor cues. These tasks span six sensory modalities, reflecting the complexity of real-world environments where beliefs are shaped by diverse perceptual inputs. Our empirical experiments evaluate state-of-the-art LLMs under zero-shot and chain-of-thought prompting, revealing insights into their ability to handle dynamic belief updates and filter irrelevant sensory information. To the best of our knowledge, BC-ToM is the first benchmark to evaluate LLMs’ ToM reasoning from a multi-sensory perspective, offering a more realistic assessment of their social reasoning capabilities.

BC-ToM is designed to measure how well LLMs’ can detect and identify belief changes in response to perceptual information. BC-ToM presents story scenarios where human protagonists hold initial beliefs and encounter perceptual cues about an event that happens in their surroundings. Based on these perceptual cues, which either modify or do not modify the protagonist’s initial beliefs, LLMs are asked to (1) detect whether the protagonist’s belief changes and (2) identify the updated beliefs.

New direction: This project is near completion, but there are some changes that need to be change. Recently, we decided that instead of just focusing on belief changes, we want to investigate a broader concept: evaluating the robustness of LLMs' theory of mind abilities, with regards to changes in beliefs. With this in mind, we have developed 3 parts for our benchmark: 
- Part 1. To what extent do changes in another person's beliefs affect the LLM's theory of mind abilities? We will investigate this by comparing the LLM's F1 score on different tasks in the original BigToM and OpenToM benchmarks with the F1 score when we introduce changing beliefs to the protagonists of each story. For simplicity, we will call this part "Task 0". 
- Part 2. We ask the LLM to perform two tasks. Task 1 is Belief Change Detection, i.e., asking LLMs to detect whether a person changes their belief after encountering a perceptual cue. Task 2 is New Belief Identification, i.e., asking LLMs to identify the person’s new belief after encountering a perceptual cue.
- Part 3. We ask the LLM to perform the same tasks under a noisy setting with several different perceptual cues. 

**About the code**
Please refer to "project_code.ipynb" for the main code of my project. This Jupyter Notebook includes a step-by-step guide of how to produce all the results in my report. 

The file "bigtom_story_scenarios.csv" is a processed version of all 200 story scenarios in the BigToM dataset.

The file "labelled_processed_percepts.csv" is a processed, filtered, and labelled version of the percept cues I have generated for my evaluation framework.

The folder "prompt_templates" refers to all the prompt templates I have used in the project. There are two prompt templates for story generation, four prompt templates for Task 1, and four prompt templates for Task 2.

The folder "evaluation_results" stores the evaluation results for Tasks 1 and 2. Files with the suffix "_total" store the number of times the LLM is queried for each percept cue, and files with the suffix "_correct" store the number of instances where the LLM answered the queries correctly.
