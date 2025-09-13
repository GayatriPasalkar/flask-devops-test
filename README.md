\# Flask DevOps Test Repository



This is a simple Flask application for testing an End-to-End DevOps CI/CD pipeline.



\## Structure23:50 13-09-2025



\- `app.py` → Simple Flask application

\- `requirements.txt` → Python dependencies

\- `test\\\_app.py` → Unit test for the Flask app

\- `sonar-project.properties` → SonarQube configuration



\## Usage



This repo is used for Jenkins pipeline to:



1\. Checkout code

2\. Install dependencies

3\. Run unit tests

4\. Run SonarQube analysis

5\. Push metrics to monitoring tools



