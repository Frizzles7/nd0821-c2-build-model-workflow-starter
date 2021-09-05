# Build an ML Pipeline for Short-Term Rental Prices in NYC
You are working for a property management company renting rooms and properties for short periods of 
time on various rental platforms. You need to estimate the typical price for a given property based 
on the price of similar properties. Your company receives new data in bulk every week. The model needs 
to be retrained with the same cadence, necessitating an end-to-end pipeline that can be reused.

In this project you will build such a pipeline.

## Environment Setup

Make sure Conda is installed. See [https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html) to install Miniconda, if needed.

Clone this repository.

Create an environment using the ``environment.yml`` file provided in the repository and activate it:

```bash
> conda env create -f environment.yml
> conda activate nyc_airbnb_dev
```

Log in to Weights & Biases with your API key, which is available in your settings on [wandb.ai/settings](wandb.ai/settings), and using 

```bash
> wandb login [your API key]
```

## Running the Project

To run the entire project and train a model, from the root of the project, run:
```bash
>  mlflow run .
```

This will download data, perform some initial cleaning, complete data checks, split the data, and train a random forest model using the best hyperparameters found during grid search.

Individual steps can be run using the `steps` parameter on the command line, where the possible steps are "download", "basic_cleaning", "data_check", "data_split", "train_random_forest", and "test_regression_model".  One or more of these steps can be run from the root of the project using: 
```bash
> mlflow run . -P steps=download,basic_cleaning
```

**Note** that the step "test_regression_model" is not run when the entire pipeline is run above.  Instead, you must run this step after a model has been tagged as "prod" in Weights & Biases.  To do so, run:
```bash
> mlflow run . -P steps=test_regression_model
```

## Weights & Biases

Runs and artifacts can be viewed in Weights & Biases here:
[wandb.ai/frizzles7/nyc_airbnb/overview?workspace=user-frizzles7](wandb.ai/frizzles7/nyc_airbnb/overview?workspace=user-frizzles7)

## License

[License](LICENSE.txt)
