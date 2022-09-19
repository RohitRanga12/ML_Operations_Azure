# Project Title: Operationalizing Machine Learning

## Project Overview: 
- Dataset used: Bank Marketing dataset. 
- I use Azure to configure a cloud-based ML production model, deploy it, and consume it. 
- I create, publish, and consume a pipeline. 
- I demonstrate all my work by creating a README file and a screencast video.


## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

## Key Steps
<b>Step 1: Authentication</b>
- I skipped this step since I used Udacity Lab and thus could not create a Service Principal
<br>

<b>Step 2: Auto ML Experiment</b>
- Upload data (csv file) to default datastore in Azure ML studio, and register a dataset
- Create a compute instance to be used by the jupyter notebook later 
- Create a compute cluster to be used by the AutoML experiment with min nodes as 1, and max nodes as 5
- Create an AutoML experiment with the above dataset and compute cluster
<hr>
<img src="screenshots/registered_dataset.png">
<hr>
<img src="screenshots/experiment_completed.png">
<hr>
<img src="screenshots/best_model_voting_ensemble.png">
<hr>
<br>

<b>Step 3: Deploy Best Model</b>
- Once AutoML experiment completes, deploy the best model on ACI with authentication enabled
<br>

<b>Step 4: Enable Logging</b>
- Create a python virtual/conda environment with libraries required to run the scripts. Activate it.
- Download config.json from Azure ML portal and store in same folder as logs.py
- In logs.py, insert the deployment name. From terminal, run "python logs.py" to enable logging
<hr>
<img src="screenshots/app_insights_enabled.png">
<hr>
<img src="screenshots/logs_screenshot.png">
<hr>
<br>

<b>Step 5: Swagger Documentation</b>
- Copy the swagger.json URL from the deployment, use wget to download file inside 'swagger' folder
- From /swagger directory, run "bash swagger.sh" to launch docker in localhost port 10000. You can view swagger UI in localhost:10000.
- Run "python serve.py", and insert "http://localhost:8000/swagger.json" in the search bar in Swagger UI. This will show the /score endpoint
<hr>
<img src="screenshots/swagger_http_endpoints_localhost.png">
<hr>
<br>

<b>Step 6: Consume Model Endpoint</b>
- In endpoint.py, insert the scoring_uri and key from the deployment, and run "python endpoint.py"
- Benchmark endpoint: Check if Apache Benchmark is installed. In benchmark.sh, insert appropriate key and scoring_uri and run "bash benchmark.sh"
<hr>
<img src="screenshots/endpoint_script_json_output.png">
<hr>
<img src="screenshots/benchmark_results.png">
<hr>
<br>

<b>Step 7: Create, Publish, Consume Pipeline</b>
- Run the cells in the aml-pipelines-with-automated-machine-learning-step.ipynb notebook after inserting the right cluster name, experiment name, dataset name. This would create and publish pipeline. 
<hr>
<img src="screenshots/pipeline_created.png">
<hr>
<img src="screenshots/pipeline_endpoint.png">
<hr>
<img src="screenshots/bank_dataset_with_automl_module.png">
<hr>
<img src="screenshots/published_pipeline_overview_status_active.png">
<hr>
<img src="screenshots/run_details_widget_step_runs.png">
<hr>
<br>


## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
- Performed the Model Endpoint's benchmarking using Apache Benchmark (though it was optional)
