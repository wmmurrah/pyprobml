* The [scripts](https://github.com/probml/pyprobml/tree/master/scripts) folder is now deprecated. All the scripts that generated figures or were referred in the text are converted to notebooks and moved to the [notebooks/book1](https://github.com/probml/pyprobml/tree/master/notebooks/book1) folder. Several scripts that are not directly used to create figures are helper scripts to the notebooks are moved to [probml/probml-utils](https://github.com/probml/probml-utils) repo.
* The [notebooks/book1](https://github.com/probml/pyprobml/tree/master/notebooks/book1) folder contains chapter-wise notebooks used to generate figures or referred in text.
* Figures generated by multiple notebooks point to a dummy notebook with the naming convention `fig_xx_yy.ipynb` where `xx` is chapter number and `yy` is figure number. Furthermore, these dummy notebooks contain captions of figures and multiple notebook URLs. For example: https://code.probml.ai/book1/2.2
    * How to maintain this in the future? Refer to [this notebook](https://github.com/probml/pyprobml/blob/master/misc/mapping_figures_to_urls.ipynb) to see the process.
* Notebooks that are referred in multiple chapters are split into multiple replicas and kept in chapter-wise folders with the rule that only one of them has the source code, and others contain a single cell with a redirection link to that notebook. For example: 1) [original](https://github.com/probml/pyprobml/blob/master/notebooks/book1/03/gauss_infer_2d.ipynb) ;2) [dummy](https://github.com/probml/pyprobml/blob/master/notebooks/book1/04/gauss_infer_2d.ipynb)
    * How to maintain this in the future? We believe that this problem will occur when a notebook is mentioned in another chapter. A GitHub Actions workflow maintained on the `bookv2` repo will detect that the mentioned notebook is missing in the `pyprobml` repo chapter-wise folder. Subsequently, one can manually create a dummy notebook to handle this case.
* Automatic GitHub Actions workflow is active on this repo, which checks code quality with `black`, statically checks imports, and then executes all the notebooks to check the errors. In the process, it also generates latexified images that are stored in the [auto_generated_figures](https://github.com/probml/pyprobml/tree/auto_generated_figures) branch. In the end, workflow status is pushed to the [workflow_status_indicator](https://github.com/probml/pyprobml/tree/workflow_status_indicator) branch, which contains logs of failing notebooks and statistics of failing notebooks.