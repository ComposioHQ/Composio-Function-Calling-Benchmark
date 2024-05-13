
<p align="center"><a href="https://github.com/SamparkAI"><img src="https://avatars.githubusercontent.com/u/128464815?s=200&v=4" alt="Composio Logo" /></a></p>

<p align="center">
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/stargazers"><img src="https://img.shields.io/github/stars/SamparkAI/Composio-Function-Calling-Benchmark" alt="Stars Badge"/></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/network/members"><img src="https://img.shields.io/github/forks/SamparkAI/Composio-Function-Calling-Benchmark" alt="Forks Badge"/></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/pulls"><img src="https://img.shields.io/github/issues-pr/SamparkAI/Composio-Function-Calling-Benchmark" alt="Pull Requests Badge"/></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/issues"><img src="https://img.shields.io/github/issues/SamparkAI/Composio-Function-Calling-Benchmark" alt="Issues Badge"/></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/SamparkAI/Composio-Function-Calling-Benchmark?color=2b9348"></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/blob/master/LICENSE"><img src="https://img.shields.io/github/license/SamparkAI/Composio-Function-Calling-Benchmark?color=2b9348" alt="License Badge"/></a>
<a href="#"><img src="https://visitor-badge.laobi.icu/badge?page_id=SamparkAI.Composio-Function-Calling-Benchmark" alt="Visitor Badge"/></a></p></p>

# Function Calling Benchmark by [Composio](https://composio.dev)

Welcome to the official GitHub repository for the Composio's Function Calling Benchmark. This repository contains a benchmark of 50 function calling problems, each of which is designed to be solved using one of the 8 function schemas provided, which are inspired from some of ClickUp's integration endpoints. 

## Overview

The benchmark is designed to test the ability of various models to correctly call functions based on given prompts, and solve the situation in a ClickUp workspace using one of the given functions. Each question in the benchmark presents a scenario that requires the use of a specific function to solve. The function schemas provided outline the structure and parameters of the functions that can be used.

> Note that, a speciality of this benchmark is, problems are designed to test the abilities of the models to handle real world API structurs, and performance against differnet optimizations.


## Publications
* [Improving GPT 4 Function Calling Accuracy](https://blog.composio.dev/gpt-4-function-calling-example/)

## Repository Structure

- [`prompts/`](prompts/): Propmts used to check & modify the Problems and Schema.
- [`clickup_space_benchmark.json`](clickup_space_benchmark.json): The problems and correct solutions.
- [`clickup_space_schema.json`](clickup_space_schema.json): Function Schema's that the LLMs use to solve the problems of the Benchmark.
- `*.ipynb`(in relevant branches): Different optimization techniques, applied to the LLMs to check their performance against the Benchmark.

> We did the all experimentations on notebooks now, as it is easier to keep track of the results.

## Running the Benchmark

We have tested different function calling models,  Resut notebooks of which are stored in each seperate branch. 

Currently we have experimented with:
* `gpt-4o` - OpenAI - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/gpt-4o)
* `gpt-4-turbo-preview` - OpenAI - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/gpt-4-turbo-preview)
* `gpt-4-turbo` - OpenAI - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/gpt-4-turbo)
* `gpt-4-0125-preview` - OpenAI - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/gpt-4-0125-preview)
* `claude-3-haiku-20240307` - Anthropic - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/claude-3-haiku-20240307)
* `claude-3-sonnet-20240229` - Anthropic - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/claude-3-sonnet-20240229)
* `claude-3-opus-20240229` - Anthropic - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/claude-3-opus-20240229)

### We are planning to add these models in future:
- [Functionary](https://github.com/MeetKai/functionary) Models(MeetKai)
- [Mistral](https://mistral.ai/) Models
- [Open-Gorilla](https://gorilla.cs.berkeley.edu/) Models
- [NexusRaven](https://github.com/nexusflowai/NexusRaven) Models
  
## Experiments

All these different optimizations has been tested with the models, and each of the techniques are explained [here](https://blog.composio.dev/gpt-4-function-calling-example/).

<img width="1106" alt="Screenshot 2024-05-14 at 12 50 49 AM" src="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/assets/67541368/26beb636-ffa6-482b-a9cd-629d096b70ff">

All previous Models: 

||Optimization Approach                                                                                                                                  |`gpt-4-turbo-preview`|`gpt-4-turbo`|`gpt-4-0125-preview`|`claude-3-haiku-20240307`|`claude-3-sonnet-20240229`|`claude-3-opus-20240229`|
|------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|-----------|------------------|-----------------------|------------------------|----------------------|
|1     |No System Prompt                                                                                                                                       |0.36               |0.36       |0.353             |0.48                   |0.6                     |0.42                  |
|2     |Flattening Schema                                                                                                                                      |0.527              |0.487      |0.533             |0.5                    |0.58                    |0.5                   |
|3     |Flattened Schema  + <br> Simple System Prompt                                                                                                                |0.553              |0.533      |0.54              |0.54                   |0.6                     |0.54                  |
|4     |Flattened Schema  + <br> Focused System Prompt                                                                                                               |0.633              |0.633      |0.64              |0.54                   |0.54                    |0.54                  |
|5     |Flattened Schema  + <br> Focused System Prompt  + <br> Function Name Optimized                                                                                     |0.553              |0.607      |0.587             |0.52                   |0.62                    |0.52                  |
|6     |Flattened Schema  + <br> Focused System Prompt  + <br> Function Description Optimized                                                                              |0.633              |0.66       |0.673             |0.52                   |0.6                     |0.52                  |
|7     |Flattened Schema  + <br> Focused System Prompt containing Schema summary                                                                                     |0.64               |0.553      |0.64              |0.46                   |0.62                    |0.46                  |
|8     |Flattened Schema  + <br> Focused System Prompt containing Schema summary  + <br>  Function Name Optimized                                                          |0.70               |0.707      |0.686             |0.5                    |0.64                    |0.46                  |
|9     |Flattened Schema  + <br> Focused System Prompt containing Schema summary  + <br>  Function Description Optimized                                                   |0.687              |0.707      |0.68              |0.5                    |0.6                     |0.6                   |
|10    |Flattened Schema  + <br> Focused System Prompt containing Schema summary  + <br>  Function and Parameter Descriptions Optimized                                    |0.767              |0.767      |0.787             |0.58                   |0.74                    |0.58                  |
|11    |Flattened Schema  + <br> Focused System Prompt containing Schema summary  + <br>  Function and Parameter Descriptions Optimized  + <br> Function Call examples added     |0.693              |0.6        |0.707             |0.6                    |0.76                    |0.64                  |
|12    |Flattened Schema  + <br> Focused System Prompt containing Schema summary  + <br>  Function and Parameter Descriptions Optimized  + <br> Function Parameter examples added|0.787              |0.693      |0.787             |0.68                   |0.76                    |0.66                  |



## Contributing

We welcome contributions to this repository. If you have a model that you would like to test against the benchmark, feel free to open a pull request. If you encounter any issues while using the benchmark, please open an issue.

## License

This project is licensed under the terms of the MIT license.

## About Composio

Composio is an organization dedicated to advancing the field of artificial intelligence. We create benchmarks, develop models, and build tools to push the boundaries of what is possible in AI. Follow us on [Twitter](https://twitter.com/composiohq) for updates on our latest projects.

---

© 2024 Composio, All Rights Reserved.
