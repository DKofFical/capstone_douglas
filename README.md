**Welcome to this project. Here are a few instructions before you start. **

**ABOUT THE RESEARCH**

**Abstract:** Large language models (LLMs) are increasingly integrated into human-facing applications, making it critical to evaluate their social reasoning capabilities, particularly their ability to understand and predict human mental states—a core aspect of the Theory of Mind (ToM). While existing benchmarks demonstrate that LLMs can achieve near-human performance in static, isolated scenarios, they fall short of capturing the dynamic nature of real-world belief formation, where human beliefs evolve in response to perceptual experiences. To address this gap, we introduce BC-ToM, a novel evaluation framework designed to assess LLMs’ ability to detect and identify belief changes triggered by multi-sensory perceptual cues. The benchmark evaluates LLMs through three tasks: (1) detecting belief changes, (2) identifying updated beliefs, and predicting belief changes in noisy settings with distractor cues. These tasks span six sensory modalities, reflecting the complexity of real-world environments where beliefs are shaped by diverse perceptual inputs. Our empirical experiments evaluate state-of-the-art LLMs under zero-shot and chain-of-thought prompting, revealing insights into their ability to handle dynamic belief updates and filter irrelevant sensory information. To the best of our knowledge, BC-ToM is the first benchmark to evaluate LLMs’ ToM reasoning from a multi-sensory perspective, offering a more realistic assessment of their social reasoning capabilities.

BC-ToM is designed to measure how well LLMs’ can detect and identify belief changes in response to perceptual information. BC-ToM presents story scenarios where human protagonists hold initial beliefs and encounter perceptual cues about an event that happens in their surroundings. Based on these perceptual cues, which either modify or do not modify the protagonist’s initial beliefs, LLMs are asked to (1) detect whether the protagonist’s belief changes and (2) identify the updated beliefs.

**New direction:** This project is near completion, but there are some changes that need to be change. Recently, we decided that instead of just focusing on belief changes, we want to investigate a broader concept: evaluating the robustness of LLMs' theory of mind abilities, with regards to changes in beliefs. With this in mind, we have developed 3 parts for our benchmark: 
- Part 1. To what extent do changes in another person's beliefs affect the LLM's theory of mind abilities? We will investigate this by comparing the LLM's F1 score on different tasks in the original BigToM and OpenToM benchmarks with the F1 score when we introduce changing beliefs to the protagonists of each story. For simplicity, we will call this part "Task 0". 
- Part 2. We ask the LLM to perform two tasks. Task 1 is Belief Change Detection, i.e., asking LLMs to detect whether a person changes their belief after encountering a perceptual cue. Task 2 is New Belief Identification, i.e., asking LLMs to identify the person’s new belief after encountering a perceptual cue.
- Part 3. We ask the LLM to perform the same tasks under a noisy setting with several different perceptual cues. 

**ABOUT THE CODE**

The main code of the project is in these files:
- create_dataset.ipynb <-- Code for creating the BC-ToM dataset from BigToM and OpenToM. This Jupyter Notebook includes a step-by-step guide on how to construct the dataset. 
- run_experiment_task_0.ipynb, run_experiment_tasks_1-4.ipynb, run_experiment_tasks_1-4.ipynb, run_experiment_tasks_1-4_deepseek_version.ipynb <-- Code for running the experiments with different LLMs on the BC-ToM benchmark. The Deepseek Version is the same as the original version, but modified because the API calls are different.
- visualize_result.ipynb <-- Code for visualizing the LLM's accuracy scores.

The datasets used in the BC-ToM benchmark are stored in the "datasets" folder:
- "llm_ready_bigtom_vfin.jsonl" and "llm_ready_opentom_vfin.jsonl" are the raw, annotated, unfiltered BC-ToM datasets.
- "bigtom_filter" and "opentom_filter" are masks that you need to use to obtain the labelled BC-ToM datasets. You can just use these masks to index the instances that are part of the dataset.
- "bigtom-modified.csv" is a CSV version of the BigToM dataset downloaded from the original authors' repository.

The experiment results are stored in the "experiment_results" folder:
- These results are stored in this format: <bigtom/opentom>_<task_number>_ans_<model_name>
- For Task 0, notice that there are results for "before belief change" and "after belief change". For the former, we ask the LLM to perform various tasks in BigToM and OpenToM without belief change - this is used as a control experiment. Meanwhile, for the latter, we ask the LLM to perform various tasks in BigToM and OpenToM after introducing belief change. This is to see if LLMs' ToM abilities are robust to changing beliefs.
- For Tasks 1-4, you may need to redo some experiments. This is because these experiments are performed on an old version of the dataset. I have updated new instances to the ".jsonl" files - just make sure to check and see if any instances are missing in the files for experiment results.

You can find the prompt templates I used in the "prompt_templates" folder. For each dataset, there are two kinds of prompts: story generation prompts (for which the file name starts with "story_generation") and question answering prompts (which are used for evaluating the LLM on the BC-ToM benchmark.)

You will also find another folder called "experiment_utils" with two "runnable filters". As our dataset contains a large number of easy negative samples, these masks are used during experiments to perform random sampling. This will make the accuracy and F1 scores less sensitive to class imbalance. 


**Other useful links**
- Overleaf link: https://www.overleaf.com/read/srhzwtzmmjgt#ea4861 <-- this includes a rough draft for some parts of the paper, but more modifications will be needed: figures need to be more presentable, citations need to be added, need additional parts such as "Error Analysis" and "Data Contamination", etc.
- Experiment Results: https://docs.google.com/spreadsheets/d/1b74RuzRNN4O8p5WBPpG3DjrPuzac9SjOM7siZnpAJJ0/edit?usp=sharing <-- as mentioned earlier, you will need to redo some experiments for Tasks 1-4 and restructure the experiment results, because they were done on an old version of the dataset. 
- BigToM: https://arxiv.org/pdf/2306.15448
- OpenToM: https://arxiv.org/pdf/2402.06044

**Wish you all the best if you will be continuing this project!**
