#local runtime
pip install virtualenv
 brew install python@3.9
python3.9 -m venv gemini-streamlit
gcloud config set project bagchi-genai-bb
gcloud auth application-default login
gcloud auth application-default set-quota-project bagchi-genai-bb
pip install -r requirements.txt
  
streamlit run home.py \
  --browser.serverAddress=localhost \
  --server.enableCORS=false \
  --server.enableXsrfProtection=false \
  --server.port 8080



gcloud builds submit --tag gcr.io/bagchi-genai-bb/gaming-3d-assset
gcloud run deploy finance-advisor-app --image gcr.io/bagchi-genai-bb/gaming-3d-assset --platform managed  --allow-unauthenticated  --region us-central1

