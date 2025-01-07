# Hugging Face Model Deployment to Elasticsearch Cloud

This repository provides scripts and instructions for deploying Hugging Face models into Elasticsearch instances hosted on Elastic Cloud. The deployment process enables advanced text embedding capabilities powered by pre-trained models.

---

## Features

- **Elastic Cloud Deployment**: Deploy models into the Elasticsearch instance hosted on Elastic Cloud.
- **Hugging Face Integration**: Leverage pre-trained models from Hugging Face for text embedding tasks.

---

## Prerequisites

1. **Python 3.x**: Ensure Python is installed on your system.
2. **Elasticsearch 8.x or later**:
   - Create an Elastic Cloud account and obtain your cloud credentials.
3. **Dependencies**:
   - Install required Python libraries directly in the notebook:
     ```bash
     !pip install eland elasticsearch
     !pip install elasticsearch
     !pip install -qU elasticsearch sentence-transformers==2.7.0
     ```

---

## Repository Structure

```plaintext
elasticsearch-model-deployment/
|
├── README.md                 # Project description and usage guide
├── .gitignore                # Ignore unnecessary files
├── elastic_cloud_deployment.ipynb  # Notebook for Elastic Cloud deployment
```

---

## Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/elasticsearch-model-deployment.git
   cd elasticsearch-model-deployment
   ```

2. **Run the Notebook**:
   Open `elastic_cloud_deployment.ipynb` in your Jupyter Notebook or JupyterLab environment.

---

## Usage

### Deploy to Elastic Cloud

The deployment process for Elastic Cloud is provided as a Jupyter Notebook. Follow these steps:

1. Install Dependencies:
   ```bash
   !pip install eland elasticsearch
   !pip install elasticsearch
   !pip install -qU elasticsearch sentence-transformers==2.7.0
   ```

2. Import Required Libraries:
   ```python
   from elasticsearch import (Elasticsearch, helpers)
   from sentence_transformers import SentenceTransformer
   import subprocess
   ```

3. Use the following example code to deploy the model:
   ```python
   # Elastic Cloud connection details
   ELASTIC_CLOUD_ID = "elastic-cloud-id"
   ELASTIC_USERNAME = "elastic"  # Default admin username
   ELASTIC_PASSWORD = "elastic-pass"

   # Model details for deployment
   MODEL_ID = "sentence-transformers__all-minilm-l6-v2"  # Unique model ID in Elasticsearch
   HUB_MODEL_ID = "sentence-transformers/all-MiniLM-L6-v2"  # Model from Hugging Face Hub

   # Command to import and deploy the model into Elasticsearch for text embedding tasks
   command = f"""
   eland_import_hub_model \
       --cloud-id {ELASTIC_CLOUD_ID} \
       --es-username {ELASTIC_USERNAME} \
       --es-password {ELASTIC_PASSWORD} \
       --hub-model-id {HUB_MODEL_ID} \
       --task-type text_embedding \
       --clear-previous \
       --start
   """

   # Run the command to deploy the model
   subprocess.run(command, shell=True, check=True)
   ```

4. Notes:
   - Replace `HUB_MODEL_ID` with another Hugging Face model ID to deploy a different model.
   - Ensure the chosen model supports the required task type (e.g., text_embedding).

---

## Requirements

- **Python Libraries**:
  - `eland`
  - `elasticsearch`
  - `sentence-transformers`
- **Hugging Face Model**: Pre-trained model ID from Hugging Face (e.g., `sentence-transformers/all-MiniLM-L6-v2`).

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contributions

Contributions are welcome! Please submit a pull request or raise an issue for enhancements or bug fixes.

---

Happy Deploying! 🚀

