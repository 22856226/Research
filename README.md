# Benchmark and Enhancement Framework for Causal Understanding in LLMs

## Overview

This repository provides the datasets, prompt files, and code used to evaluate and enhance the causal reasoning abilities of Large Language Models (LLMs). The project focuses on leveraging **Directed Acyclic Graphs (DAGs)** and structured fine-tuning to test and improve the causal reasoning capabilities of LLMs.

The framework is divided into three main contributions:

1. Development of a benchmark dataset grounded in causal graph principles.
2. Structured fine-tuning with instruction-based prompts to enhance reasoning capabilities.
3. Evaluation using the CLADDER dataset, reformatted for structural testing.

---

## Datasets

The dataset includes the following files:

1. **`ground_truth_nodes.csv`**  
   Contains the nodes of the DAGs used in the benchmark.

2. **`ground_truth_edge.csv`**  
   Contains the direct causal edges from the DAGs, serving as the ground truth for causal relationships.

3. **`edges_with_collider.csv`**  
   Edges representing collider relationships extracted in Step 2 of our methodology by combining graph theory with direct edges.

4. **`edges_with_confounder.csv`**  
   Edges representing confounder relationships extracted using the same process.

5. **`edges_with_mediation.csv`**  
   Edges representing mediator relationships derived from the causal graphs.

6. **`KnowledgeChallenge_Set.csv`**  
   Atomic pairs containing:
   - **Ground Truth Edges**: Correct causal relationships.
   - **Incorrect Edges**: Misleading or incorrect relationships.  
   This dataset is used to evaluate whether LLMs possess the foundational causal knowledge.

---

## Prompt Files

### For Baseline Testing:
- **`mediator_prompt.csv`**  
- **`confounder_prompt.csv`**  
- **`collider_prompt.csv`**  

These files contain prompts to test the reasoning ability of LLMs by asking them to identify mediators, confounders, and colliders.

### For Structured Fine-Tuning:
- **`mediator_prompt1.csv`**  
- **`confounder_prompt1.csv`**  
- **`collider_prompt1.csv`**  

These files are reformatted into **instruction-based prompts** containing:
  - **<thinking>:** Guides step-by-step reasoning.
  - **<reflection>:** Encourages error recognition and self-correction.
  - **<output>:** Captures the final response.  

After fine-tuning on a few examples, these structured prompts are used to test the causal reasoning abilities of LLMs.

---

## Evaluation Datasets

### Rung 1, Rung 2, Rung 3  
These files contain questions from the **CLADDER dataset** reformatted into our structural prompt format for testing advanced causal reasoning tasks. The dataset evaluates LLMs' performance on associational, interventional, and counterfactual reasoning tasks.

---

## Model Outputs

The repository includes responses from each model tested:

1. **`Gemma2_9B`**  
   Represents the **vanilla model** performance without any fine-tuning.

2. **`Gemma2_9B_Tuned_with_Pair_Knowledge`**  
   Model fine-tuned using **atomic pairs** from `KnowledgeChallenge_Set.csv`.

3. **`Gemma2_9B_reflection_tuning`**  
   Model fine-tuned using from examples from the **instruction-based prompts** (`*_prompt1.csv`)   

Each model's responses demonstrate the progressive improvement in causal reasoning capabilities.

---

## Code Files

The repository includes Two Jupyter Notebooks: Deploys the models and configures them for testing.



## Contributions

### First Contribution
- Creation of a benchmark dataset with over **2,000 causal structural questions**.
- Testing LLMs' ability to identify mediators, confounders, and colliders using direct and constructed causal edges.

### Second Contribution
- Instruction-based fine-tuning with **few-shot learning**.
- Structured prompts designed to improve reasoning through:
  - Step-by-step guidance.
  - Error recognition and self-correction.

### Third Contribution
- Evaluation using the **CLADDER dataset** reformatted into the structural prompt format.
- Comparison with state-of-the-art models and methods.






