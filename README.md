# Reynard Experiment Artifacts

This repository contains the raw data used to generate the results, as well as files generated based on the raw data using the scripts available in the [main repository](https://github.com/reynard-testing/reynard).

## File structure

- `/filibuster` - Logs of running _filibuster_ on the _filibuster corpus_ with the same failure modes as Reynard.
  - `/with[out]-SER` - Results with dynamic reduction/SER (Service Encapsulation Reduction) enabled.
    When disabled, only benchmarks are included where SER had a reduction when enabled.
    Only one iteration is included when disabled, because only the case count is used in the results.
    - `/<benchmark>/cases.out` extracted numbers of tests generated.
    - `/<benchmark>/timings.out` extracted elapsed time (as reported by filibuster).
    - `/<benchmark>/<iteration>/filibuster.log` the raw logs of filibuster. Note that to reduce the size (and effect on efficiency) only log levels _INFO_ and up are reported.
- `/reynard` - Reynard experiments
  - `/benchmarks` - Tests on specific benchmark systems
    - `/logs` - The raw logs reported when Reynard is run. Mostly contains reports on found anti-patterns on a per test case basis, but can be used as a reference.
    - `/with[out]-SER` - Similar to the filibuster results, either with or without SER enabled.
      - `<benchmark-system>/<test-case>/` contains the processed results that process all iterations. The seperate results per iteration can be found in the number subdirectories and corresponding json files.
  - `/overhead` - Benchmark for measuring the overhead
    - `<scenario>/` - Specific scenarios as [detailed here](https://github.com/reynard-testing/reynard/tree/main/util/experiments/overhead).
      - `default<x>` - An iteration of each benchmark
      - `<x>.out` Collected values from each iteration
      - `<x>.avg` Averages of the values collected in the `.out` files
