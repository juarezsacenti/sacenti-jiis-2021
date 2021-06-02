# sacenti-jiis-2021
Results from the paper Sacenti, et al. (2021), to appear in the Journal of Intelligent Information Systems

These results were generated by Knowledge Graph (KG) -based Summarization (Summ.) and Recommendation (Rec) [project](https://github.com/juarezsacenti/kg-summ-rec).
It implements and evaluates the KGE-K-Means Summarization method proposed in our paper, which combines KG Embedding (ComplEx) with node clustering (K-Means).

We summarize two datasets, Sun and Cao, that enrich MovieLens 1M user-item interactions with side information about movies from IMDb and DBpedia, respectively.
Three experimental scenarios were defined. The first scenario, <em>exp1</em>, adopts Sun's dataset, hold-out with random partitioning of user-item interactions following the proportions of 7:1:2 for training, validation, and test, respectively, and the RS model training uses an early-stopping strategy. The script of this experiment is available in the [kg-summ-rec project](https://github.com/juarezsacenti/kg-summ-rec/examples/Sacenti-JIIS2021-revised/run_exp1-sun_ho_complex.sh).

The second scenario, <em>exp2</em>, adopts Sun's dataset, 5-fold cross-validation with random partitioning of user-item interactions following the proportions of 6:2:2 for training, validation, and test, respectively, and the RS model training uses a fixed number of epochs. The script of this experiment is available in the [kg-summ-rec project](https://github.com/juarezsacenti/kg-summ-rec/examples/Sacenti-JIIS2021-revised/run_exp2-sun_cv_complex.sh).

The third scenario, <em>exp3</em>, adopts Cao's dataset, hold-out with random partitioning of user-item interactions following the proportions of 7:1:2 for training, validation, and test, respectively, and the RS model training uses an early-stopping strategy. The script of this experiment is available in [kg-summ-rec project](https://github.com/juarezsacenti/kg-summ-rec/examples/Sacenti-JIIS2021-revised/run_exp3-cao_ho_complex.sh).

In all scenarios, we evaluate 2 GS approaches: single-view (sv) and multi-view (mv); and 4 KG-based RS: CFKG, CKE, CoFM and KTUP. Also, all KGs were summarized considering their item-graph (ig) representation, i.e. the KG only contains items and side information about items. In <em>exp1</em>, we evaluate 3 preprocessing methods: entity filtering (fKG), proposed GS (sKG), and both (sfKG), while <em>exp2</em> and <em>exp3</em> only evaluate the proposed GS (sKG). In <em>exp1</em> and <em>exp2</em>, we evaluate 3 summarization ratios: 75%, 50%, and 25%, while <em>exp3</em> evaluates only summarization ratio at 75%.

Please note that we use retention ration instead of summarization ratio in our implementation and directory naming. Retention ratio (<em>r</em>) is the complement of summarization ratio (<em>s</em>), i.e. <em>r = 1 - s</em>.

Project <em>kg-summ-rec</em> also provide a fourth scenario, <em>exp4</em>, that adopts Cao's dataset, 5-fold cross-validation with random partitioning of user-item interactions following the proportions of 6:2:2 for training, validation, and test, respectively, and the RS model training uses a fixed number of epochs. Although its results are not present in the paper, we provide them as a complement of <em>exp3</em>.


## Content

We summarize the content of this project as follows:

```
git
└─datasets
| └─ml-cao_oKG
| └─ml-sun_oKG
| | └─kg-ig.nt
| └─exp2-sun_cv
| | └─folds
| └─exp4-cao_cv
└─results
| └─exp1-sun_ho
| | └─overall_comp_cost.tsv
...
| | └─ml-sun_ho_sKG_ig-sv-complex-25
| | | └─comp_cost.tsv
| | | └─kg-ig_stats.tsv
| | | └─*.log
| | | └─*.dat
| └─exp2-sun_cv
| └─exp3-cao_ho
| └─exp4-cao_cv
```

Files <em>kg-ig.nt</em> contain the KG in N-triples format. Folder <em>folds</em> contains files <em>sun\_fold\*.dat</em> with splitted data. 
Files <em>overall\_comp\_cost.tsv</em> contain the duration of each task that was collected by the script. Files <em>comp\_cost.tsv</em> contain the duration of RS model training extracted from log files. Note that we adopt the durations of <em>overall\_comp\_cost.tsv</em>.
Files <em>kg-ig\_stats.tsv</em> contain the KG statistics. Files <em>\*.log</em> contain the log of training models with quality results. Files <em>\*.dat</em> contain the list of predictions in the form of user-item-score. Folders <em>exp2-sun\_cv</em> and <em>exp4-cao_cv</em> have a different structure due to 5 fold cross-validation.

In our paper, the results of exp1 generated tables 2 and 3 and figures 5, 7, and 8. The results of exp2 generated table 4 and figure 6. The results of exp3 were cited in section 6.

## Environment
These results were generated on a machine with an Intel(R) Xeon(R) CPU E5-2640 v4 @ 2.40GHz, 10 physical cores (HT enabled), L1 cache: 32KB data, 32KB instruction per core, L2 cache: 256KB per core, L3 cache: 25MB accessible by all CPU core, NUMA nodes: 2 (20 physical cores + HT), 128 GB of RAM, NVIDIA Tesla K40c, running the linux Ubuntu 16.06 x86_64.
