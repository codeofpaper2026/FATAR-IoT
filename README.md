# FATAR-IoT: code and datasets

Download [FATAR-IoT.zip](FATAR-IoT.zip) and extract it. The archive contains the Python implementation, configurations, tests, the original **RT-IoT2022 dataset**, and a synthetic dataset.

## Run an experiment

From the extracted `FATAR-IoT` directory (Python 3.11+):

```bash
python -m pip install -r requirements.lock.txt
python -m pip install --no-deps -e .
python -m pytest -q
python scripts/check_release.py
python -m fatr_iot run --config configs/rt_iot2022.yaml --output outputs/rt_iot2022 --plots
python scripts/verify_real_data_results.py --input outputs/rt_iot2022
```

Use a new or empty output folder. Experiment outputs are generated locally; saved results, plots, trained models and logs are not included in this distribution. Detailed methods and configurations are inside the archive.

This is a new reference implementation of FATR's mathematical design. It does not reconstruct the original manuscript's synthetic experiment. The geometry_trust comparator is not the original TrustFedAvg. Binary classification, logistic regression and randomized row splits do not establish deployment, unseen-device or chronological generalization.

## Dataset attribution and license

**RT-IoT2022**, 123,117 original traffic records. S., B. & Nagapadma, R. (2023). UCI Machine Learning Repository. [Dataset and DOI](https://doi.org/10.24432/C5P338). [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The original CSV is unchanged. Code is MIT; this does not replace the dataset license.

The synthetic dataset and its prepared split are retained. An UNSW-NB15 adapter is included; UNSW-NB15 observations are not bundled.
