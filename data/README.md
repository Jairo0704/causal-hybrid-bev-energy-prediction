# Experimental data

The experimental dataset is intentionally **not included** in the public repository.

Authorized users should place the model-ready file locally at:

`data/BEV_model_ready_dataset.xlsx`

The repository `.gitignore` excludes experimental and derived row-level data from version control.

Do not commit:
- raw GPS coordinates or complete trajectories;
- OBD/vehicle telemetry;
- battery voltage/current measurements;
- row-level 1 Hz data;
- processed trip datasets;
- train/validation/test observation files;
- row-level model predictions.

The expected variable schema is documented in `data_schema.csv`.

The loader supports both the normalized manuscript-oriented names and the original working names:
- `Speed` → `v`
- `Acceleration` → `a`
- `Road_gradient` → `theta`
- `RPM` → `MotorSpeed`
