# kubernetes-flask-application

1. hope you have a docker image created using https://github.com/vaibhavnarkhede12/docker-flask-application repo
2. minikube start --vm-driver=docker
3. minikube dashboard // This will open up the kubernetes UI on your browser
3. minikube image load flask:0.1   // this is to ensure minkube uses image from our local docker instead of hitting dockerhub also note imagePullPolicy: Never in kflask.yaml for same 
4. kubectl apply -f flask-service.yaml
5. kubectl apply -f flask.yaml
6. minikube service kflask-service



import psycopg2
from google.cloud.sql.connector import connector

# Connection parameters
database = 'your_database_name'
cloud_sql_connection_name = 'your_cloud_sql_connection_name'  # Format: <project-id>:<region>:<instance-id>
service_account_key_file = 'path/to/your/service_account_key_file.json'

# Get the connection object using the service account credentials
conn = connector.connect(
    instance_connection_name=cloud_sql_connection_name,
    service_account_json_key_file=service_account_key_file
)

# Create the PostgreSQL connection using the Cloud SQL Connector
pg_connection = psycopg2.connect(
    dbname=database,
    user=conn.user,
    password=conn.password,
    host=conn.host,
    port=conn.port,
)

# Perform database operations using 'pg_connection', for example:
# with pg_connection.cursor() as cursor:
#     cursor.execute("SELECT * FROM your_table")
#     result = cursor.fetchall()

# Don't forget to close the connection when you're done
pg_connection.close()
