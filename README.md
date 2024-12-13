MLflow Model Deployment Progress Report
Overview
This document provides an overview of the progress made in setting up and deploying machine learning models using MLflow. The tasks include setting up the MLflow Tracking Server, logging and registering models, serving them locally, and addressing challenges encountered during the process.

Progress So Far
1. MLflow Tracking Server Setup
Successfully configured and launched the MLflow Tracking Server locally at http://127.0.0.1:5000.
Environment variables were set correctly, specifically MLFLOW_TRACKING_URI, to ensure connectivity with the tracking server.
Verified the setup by logging experiments and accessing the MLflow UI.
2. Model Training and Logging
Implemented a Linear Regression model using scikit-learn and trained it on a sample dataset.
Logged:
Model artifacts
Performance metrics
Model parameters
to the MLflow Tracking Server.
3. Model Registration
Registered the trained model in the MLflow Model Registry.
Added aliases to different model versions for tracking stages such as Production, Staging, and Testing.
Successfully verified the registered models using both the MLflow UI and the REST API.
4. Serving the Model
Deployed the registered model locally using the mlflow models serve command:
Experimented with both Flask-based and MLServer-based deployments.
Configured the inference endpoint to run on port 5000 for predictions.
Challenges Faced
1. Environment Issues
Encountered compatibility issues with Python 3.13.1 during model deployment, as MLflow did not support this version.
Resolved the issue by:
Switching to a supported Python version (3.12.x) using pyenv.
Updating the environment variables to ensure the correct Python version was used.
2. Invocation Endpoint Issues
Initially received a 404 Not Found error when testing the /invocations endpoint.
Debugging Steps:
Verified the model server was running on the correct port (5000).
Corrected the payload format and ensured the headers matched the model's expected schema.
Adjusted the input data to align with the model's signature, resolving data format-related issues.
3. Environment Variable Adjustments

Faced issues related to MLflow and Python dependencies.

Steps Taken:
Configured and updated critical environment variables (MLFLOW_TRACKING_URI, PYTHONPATH).
Made changes to .bashrc to persist environment settings across sessions.
4. Model Not Found Error
Encountered errors where MLflow could not locate the registered model, specifically:
"Could not find a registered artifact repository for: model:/basic_lr_iris_model/3".
Debugging Steps:
Ensured the MLflow Tracking URI was set to the correct server.
Verified model registration and resolved issues with the artifact repository.
Next Steps
Continue optimizing model serving and testing for robustness.
Explore batch predictions and deployment to external platforms (e.g., Kubernetes or cloud services).
Address any remaining compatibility issues to ensure smooth end-to-end MLflow workflows.
Conclusion
Significant progress has been made in understanding and deploying MLflow components, including the Tracking Server, Model Registry, and serving capabilities. The challenges faced during the process have been systematically addressed, enhancing the learning experience.
