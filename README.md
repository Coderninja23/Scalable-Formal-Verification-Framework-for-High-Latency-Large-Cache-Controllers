# Scalable Formal Verification Framework for High Latency Large Cache Controllers

This repository contains the UPPAAL models and verification queries used in the formal verification and statistical model checking experiments presented in the associated paper.

## Repository Structure

models/
    UPPAAL XML models containing timed-automata models and verification queries

results/
    Supporting experiment information and results where available.
````

## Requirements

* UPPAAL
* Java Runtime Environment compatible with the installed UPPAAL version

## Models

The `models/` directory contains the UPPAAL XML models used in the experiments. Each XML file contains both the timed-automata model and the corresponding verification queries.

The models represent the cache-controller pipeline, request generation, queue management, metadata handling, data operations, protocol-related behavior, and timing behavior.

## Main Parameters

The models are parameterized using variables including:

| Parameter           | Description                                    |
| ------------------- | ---------------------------------------------- |
| `N`                 | Number of modeled request/controller instances |
| `HIT_PERCENT`       | Cache-hit percentage                           |
| `QUEUE_CAP`         | Queue capacity                                 |
| `LAT_MIN`           | Minimum modeled request latency                |
| `LAT_MAX`           | Maximum modeled request latency                |
| `tag_count`         | Tag-related queue occupancy                    |
| `dr_count`          | Data-read queue occupancy                      |
| `dw_count`          | Data-write queue occupancy                     |
| `tw_count`          | Tag-write queue occupancy                      |
| `request_stage[i]`  | Processing stage of request `i`                |
| `latency_cycles[i]` | Latency of request `i`                         |
| `req_completed`     | Number of completed requests                   |

## Running the Models

1. Open an XML file from `models/` in UPPAAL.
2. Select the required query from the Queries panel.
3. Configure the model parameters as required.
4. Run the query using the UPPAAL verifier or statistical model checker.

The XML files contain the queries used for exhaustive verification, statistical model checking, and simulation.

## Verification

The models support:

* Safety and functional-property verification
* Deadlock checking
* Request-completion and progress checking
* Queue-bound verification
* Statistical analysis of latency and execution behavior
* Simulation and trace generation

The exact queries used for the reported experiments are contained in the corresponding XML files.

## Reproducing Experiments

To reproduce an experiment:

1. Open the corresponding XML model.
2. Set the required model parameters.
3. Select the corresponding query.
4. Run the query in UPPAAL.
5. Record the verification result and relevant configuration.

For statistical model checking, record the time horizon, number of runs, confidence level, and precision parameters used.

## Verification Time and Request Latency

Verification time refers to the wall-clock time required by UPPAAL or UPPAAL-SMC to evaluate a query.

Request latency refers to the modeled number of cycles required to process a cache request.

These are separate quantities.

## Scope

The models focus on controller-level formal verification of the cache-controller pipeline. Detailed RTL implementation behavior, complete multicore coherence interactions, and detailed NoC/DRAM behavior are outside the current model scope.

