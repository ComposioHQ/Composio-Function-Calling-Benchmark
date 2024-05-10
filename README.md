
<p align="center"><a href="https://github.com/SamparkAI"><img src="https://avatars.githubusercontent.com/u/128464815?s=200&v=4" alt="Composio Logo" /></a></p>

<p align="center">
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/stargazers"><img src="https://img.shields.io/github/stars/SamparkAI/Composio-Function-Calling-Benchmark" alt="Stars Badge"/></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/network/members"><img src="https://img.shields.io/github/forks/SamparkAI/Composio-Function-Calling-Benchmark" alt="Forks Badge"/></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/pulls"><img src="https://img.shields.io/github/issues-pr/SamparkAI/Composio-Function-Calling-Benchmark" alt="Pull Requests Badge"/></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/issues"><img src="https://img.shields.io/github/issues/SamparkAI/Composio-Function-Calling-Benchmark" alt="Issues Badge"/></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/graphs/contributors"><img alt="GitHub contributors" src="https://img.shields.io/github/contributors/SamparkAI/Composio-Function-Calling-Benchmarkp?color=2b9348"></a>
<a href="https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/blob/master/LICENSE"><img src="https://img.shields.io/github/license/SamparkAI/Composio-Function-Calling-Benchmark?color=2b9348" alt="License Badge"/></a>
<a href="#"><img src="https://visitor-badge.laobi.icu/badge?page_id=SamparkAI.Composio-Function-Calling-Benchmark" alt="Visitor Badge"/></a></p></p>

# Function Calling Benchmark by [Composio](https://composio.dev)

Welcome to the official GitHub repository for the Composio's Function Calling Benchmark. This repository contains a benchmark of 50 function calling problems, each of which is designed to be solved using one of the 8 function schemas provided, which are inspired from some of ClickUp's integration endpoints. 

## Overview

The benchmark is designed to test the ability of various models to correctly call functions based on given prompts, and solve the situation in a ClickUp workspace using one of the given functions. Each question in the benchmark presents a scenario that requires the use of a specific function to solve. The function schemas provided outline the structure and parameters of the functions that can be used.

> Note that, a speciality of this benchmark is, problems are designed to test the abilities of the models to handle real world API structurs, and performance against differnet optimizations.
> 
## Repository Structure

- [`prompts/`](prompts/): Propmts used to check & modify the Problems and Schema.
- [`clickup_space_benchmark.json`](clickup_space_benchmark.json): The problems and correct solutions.
- [`clickup_space_schema.json`](clickup_space_schema.json): Function Schema's that the LLMs use to solve the problems of the Benchmark.
- `*.ipynb`: Different optimization techniques, applied to the LLMs to check their performance against the Benchmark.

> We did the all experimentations on notebooks now, as it is easier to keep track of the results.

## Running the Benchmark

We have tested different function calling models,  Resut notebooks of which are stored in each seperate branch. 

Currently we have experimented with:
* `gpt-4-turbo-preview` - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/gpt-4-turbo-preview)
* `gpt-4-turbo` - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/gpt-4-turbo)
* `gpt-4-0125-preview` - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/gpt-4-0125-preview)
* `claude-3-haiku-20240307` - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/claude-3-haiku-20240307)
* `claude-3-sonnet-20240229` - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/claude-3-sonnet-20240229)
* `claude-3-opus-20240229` - [branch](https://github.com/SamparkAI/Composio-Function-Calling-Benchmark/tree/claude-3-opus-20240229)

## Experiments

All these different optimizations has been tested with the models, and each of the techniques are explained [here](https://blog.composio.dev/gpt-4-function-calling-example/).

| Approach | Run 1 | Run 2  | Run 3  | Average Accuracy  |
|---|---|---|---|---|
| No System Prompt  | 0.36  | 0.36  | 0.36  | 0.36  |
| Flattening Schema  | 0.54  | 0.5  | 0.54  | 0.527  |
| Flattened Schema + <br>Simple System Prompt  | 0.56  | 0.56  | 0.54  | 0.553  |
| Flattened Schema + <br>Focused System Prompt  | 0.64  | 0.64  | 0.62  | 0.633  |
| Flattened Schema + <br>Focused System Prompt containing Schema summary  | 0.64  | 0.62  | 0.66  | 0.64  |
| Flattened Schema + <br>Focused System Prompt containing Schema summary + <br>Function Name Optimized  | 0.72  | 0.72  | 0.66  | 0.70  |
| Flattened Schema + <br>Focused System Prompt containing Schema summary + <br>Function Description Optimized  |  0.68  | 0.7  | 0.68  | 0.687  |
| Flattened Schema + <br>Focused System Prompt containing Schema summary + <br>Function and Parameter Descriptions Optimized  | 0.78  | 0.76  | 0.76  | 0.767  |
| Flattened Schema + <br>Focused System Prompt containing Schema summary + <br>Function and Parameter Descriptions Optimized + <br>Function Call examples added  | 0.72  | 0.7  | 0.66  | 0.693  |
| Flattened Schema + <br>Focused System Prompt containing Schema summary + <br>Function and Parameter Descriptions Optimized + <br>Function Parameter examples added  | 0.82  | 0.76  | 0.78  | 0.787  |

## Contributing

We welcome contributions to this repository. If you have a model that you would like to test against the benchmark, feel free to open a pull request. If you encounter any issues while using the benchmark, please open an issue.

## License

This project is licensed under the terms of the MIT license.

## About Composio

Composio is an organization dedicated to advancing the field of artificial intelligence. We create benchmarks, develop models, and build tools to push the boundaries of what is possible in AI. Follow us on [Twitter](https://twitter.com/composio) for updates on our latest projects.

---

© 2024 Composio, All Rights Reserved.
