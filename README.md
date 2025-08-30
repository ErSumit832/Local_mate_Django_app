

# LocalMate.

**LocalMate** is a platform that connects travelers with local guides to discover authentic experiences, hidden spots, and the true soul of a city. Tourists can explore like locals, while guides earn by sharing their knowledge.

---

## Prerequisites.

Before you begin, make sure you have the following installed on your machine:

- [Docker](https://www.docker.com/get-started)
- [Kind](https://kind.sigs.k8s.io/) (Kubernetes in Docker)
- Python 3
- `virtualenv`

---

## Local Deployment.

1. **Create a virtual environment:**
```
   virtualenv env
```
2. Activate the environment:
```
source env/bin/activate
```

3. Install dependencies:
```
pip install -r requirements.txt
```

4. Run database migrations:
```
python3 manage.py migrate
```

5. Start the development server:
```
python3 manage.py runserver
```

## Visit to see the app locally.
```
http://127.0.0.1:8000
```
# Docker Deployment.

1. Build the Docker image:
```
docker build -t django-app .
```

2. Run the container:
```
docker run -d -p 8000:8000 django-app
```

3. Visit to see the app running in Docker.
```   
http://localhost:8000 
```

# Kubernetes Deployment.

1. Create a Kind cluster:
```
kind cluster create --name django-cluster --config=config.yml
```

2. Check cluster nodes:
```
kubectl get nodes
```

3. Deploy the application:
```
kubectl apply -f deployment.yml
```

4. Verify pods are running:
```
kubectl get pods -n django
```

5. Deploy the service:
```
kubectl apply -f service.yml
```

6. Check services:
```
kubectl get svc -n django
```

7. Port-forward the service to access the app locally:
```
kubectl port-forward service/django-service 80:80 -n django --address=0.0.0.0
```

Visit to see the deployment.
```
http://localhost:80 
```
# Notes.

Make sure your config.yml, deployment.yml, and service.yml are correctly configured for your cluster.

Use deactivate to exit the virtual environment when done.
