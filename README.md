# Geographica2

Geographica2 is a benchmark for evaluating Geospatial RDF stores.
For more details, please visit http://geographica2.di.uoa.gr/
This repository provides the configuration files for executing
this benchmark using KOBE benchmarking engine.
For instructions on how to install KOBE in your system please visit the
[GitHub page](https://github.com/semagrow/kobe/) or the
[KOBE User Guide](https://semagrow.github.io/kobe/).

## How to run the experiments

In the following, we show the steps for deploying an experiment of 

First, apply the following templates:
```bash
kubectl apply -f strabontemplate.yaml
kubectl apply -f unotemplate.yaml
```

Then, apply the *benchmark specification* of the synthetic workload:
```bash
kubectl apply -f benchmarks/synthetic/geographica-sy.yaml
```
and then proceed with the execution of the experiment with the following *experiment specification*:
```bash
kubectl apply -f experiments/geographica-sy-exp.yaml
```

You can view the experiment results using KOBE WebUI, or with
the logs of the geographica-sy-pod.

For running another experiment, delete the experiment and benchmark specifications
```bash
kubectl delete experiments.kobe.semagrow.org --all
kubectl delete benchmarks.kobe.semagrow.org --all
```
and then redo the steps from the beginning for running another workload.

Available benchmark specifications (with the corresponding experiment specification):

Benchmark specification | Experiment specification  | Description
:-----------------------|:--------------------------|:-----------
`benchmarks/synthetic/geographica-sy.yaml`       | `experiments/geographica-sy-exp.yaml` | Synthetic workload
`benchmarks/real-world/geographica-rw1.yaml`     | `experiments/geographica-rw-exp.yaml` | Real-world workload (part 1)
`benchmarks/real-world/geographica-rw2-pt1.yaml` | `experiments/geographica-rw-exp.yaml` | Real-world workload (part 2)
`benchmarks/real-world/geographica-rw2-pt2.yaml` | `experiments/geographica-rw-exp.yaml` | Real-world workload (part 3)
`benchmarks/real-world/geographica-rw2-pt3.yaml` | `experiments/geographica-rw-exp.yaml` | Real-world workload (part 4)
`benchmarks/real-world/geographica-rw3.yaml`     | `experiments/geographica-rw-exp.yaml` | Real-world workload (part 5)
`benchmarks/real-world/geographica-rw4.yaml`     | `experiments/geographica-rw-exp.yaml` | Real-world workload (part 6)
`benchmarks/scalability/geographica-sc-10K.yaml` | `experiments/geographica-sc-exp.yaml` | Scalability workload (10K dataset)
`benchmarks/scalability/geographica-sc-100K.yaml`| `experiments/geographica-sc-exp.yaml` | Scalability workload (100K dataset)
`benchmarks/scalability/geographica-sc-500M.yaml`| `experiments/geographica-sc-exp.yaml` | Scalability workload (500M dataset)
`benchmarks/scalability/geographica-sc-1M.yaml`  | `experiments/geographica-sc-exp.yaml` | Scalability workload (1M dataset)
`benchmarks/scalability/geographica-sc-10M.yaml` | `experiments/geographica-sc-exp.yaml` | Scalability workload (10M dataset)
`benchmarks/scalability/geographica-sc-100M.yaml`| `experiments/geographica-sc-exp.yaml` | Scalability workload (100M dataset)

## Results

In the ./results directory you can view several screenshots of the Kibana dashboards for sample executions.
