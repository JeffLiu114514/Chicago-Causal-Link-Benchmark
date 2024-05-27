Chicago Causal Link Benchmark
==============================================

This is an open-source benchmark for evaluating causal link discovery. All datasets used in the benchmark are from [Chicago Data Portal](https://data.cityofchicago.org/). This benchmark is a part of our contribution in our HILDA@SIGMOD 2024 paper "Causal Dataset Discovery with Large Language Models"(in submission). When using the benchmark, make sure to refer to it as follows:

```TeX
@inproceedings{liu2024causallink,
  author    = {Junfei Liu and
               Shaotong Sun and
               Fatemeh Nargesian},
  title     = {Causal Dataset Discovery with Large Language Models},
  year      = {2024}
}
```

Benchmark Overview
=========
Three micro-benchmarks are created independently with a disjoint set of tables. 

Benchmark\#1 includes 20 relatively large tables, each containing on average 34 columns and 46,963 rows, designed to simulate intensive datasets with high joinability and dense potential causal links.

Benchmark\#2 includes 40 smaller tables with on average 12 columns and 14,993 rows, designed to simulate datasets with small tables thus low joinability and sparse potential causal links.

Benchmark\#3, the largest datasets, includes 64 tables, which contains all tables in benchmarks\#1 and \#2, with on average 22 columns and 42,316 rows. All three micro-benchmarks cover all public data categories to comprehensively represent diverse data sources in large data repositories.

|                                  | Benchmark\#1 | Benchmark\#2 | Benchmark\#3 |
|----------------------------------|-----------------------|-----------------------|-----------------------|
| \# of source tables              | 20                    | 40                    | 64                    |
| % avg \# of columns              | 34                    | 12                    | 22                    |
| % avg \# of rows                 | 46963                 | 14993                 | 42316                 |
| total \# of pairs w/o duplicates | 1095                  | 1265                  | 1838                  |
| \# of pairs pass MI threshold    | 312                   | 405                   | 668                   |
| \# of Positive causal relations  | 61                    | 12                    | 78                    |


How to Use
=========
We provide three files for each benchmark: `bench_newlabels.json`, `benchmark_all_vars.csv`, and `sketch_bench.csv`.

`sketch_bench.csv` contains the raw information obtained through correlation sketching(Santos et al., [2021](http://dx.doi.org/10.1145/3448016.3458456)) of all raw candidate pairs, which is the output of candidates generation step refered in the paper. Each row in the file includes all statistical measurements of each column pair, including mutual information(mi_est stands for MI simulated through sketch,mi_actual stands for MI calculated through join).

`bench_newlabels.json` contains the column pair information and mutual information extracted from `sketch_bench.csv` and ground truth of causal links after duplicate filtering. 

`benchmark_all_vars.csv` contains the correlation links, which include column pair information and ground truth of causal links after MI thresholding of 0.501.

`bench_newlabels.json` and `benchmark_all_vars.csv` are the files that should be easily read and used.
