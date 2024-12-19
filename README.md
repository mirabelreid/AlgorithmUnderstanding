# AlgorithmUnderstanding
Supplementary material for the paper Does GPT Really Get It? A Hierarchical Scale to Quantify Human and AI's Understanding of Algorithms. Includes the full set of questions used for evaluation and sample responses. 


### Further details on LLM experiments
In each experiment on GPT, the query included a system prompt to encourage the model to produce only relevant information. The system prompts used in the experiments are as follows: 

'You will answer a series of questions related to computing the maximum flow on a directed graph. You provide concise responses and do not include detail or explanations unless explicitly requested by the user.'
'You will answer a series of questions related to the Euclidean algorithm for computing the greatest common divisor (gcd) of two integers. You provide concise responses and do not include detail or explanations unless explicitly requested by the user.'


GPT was queried via the OpenAI Chat Completions API using the default parameters (e.g. temperature=1). Specific versions queried are `gpt-3.5-turbo-0125',`gpt-4-turbo-2024-04-09', and `gpt-4o-2024-05-13'. 

We conducted two experiments with GPT. In the first, GPT was asked randomized versions of the questions given to students (a *quiz*), with the images being replaced with text descriptions of the graphs. For each quiz, the questions corresponding to each of the levels of understanding were asked in order, and the previous questions and responses were included in the API query. This quiz was repeated thirty times for each GPT version and algorithm. All trials were hand-graded on a scale from zero to two. 

In the second experiment, GPT was queried with only the simple and intermediate evaluation questions for Max Flow (with varying graph structure and random weights). In one trial, GPT was first asked the simple question followed by the intermediate (with its response to the simple question passed to the API in the chat history). In the second trial, a sample response to an intermediate evaluation was passed to the chat history. The responses were checked by hand for correctness, and the rate of correctness was recorded. 

### Further details on Evaluation
Human and LLM responses were evaluated with the same criteria.
* For Level 1 (Simple Evaluation) and Level 2 (Step-by-Step Evaluation), the response was given a score of 2 if the answer was correct. A score of 1 was given if the answer was incorrect due to at most one calculation error.
* For Level 3 (Code Representation) questions, the response was given a score of 2 if the code correctly computed the output for all inputs. A score of 1 was given if the code was conceptually correct with some minor error (e.g., forgetting to initialize a variable). Minor syntactical errors were ignored.
* For Level 4a (Example) and 5a (Counterexample/Extrapolation), a score of 2 was given for a correct example, and a score of 1 was given if the example was incorrect due to at most one calculation error.
* Level 4b (Explanation) and 5b (Counterfactual Question) were graded as described in the “Evaluation” section of the paper.
