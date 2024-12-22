FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
COPY devops ./devops/

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 8000
ENTRYPOINT ["python3"]
CMD ["devops/manage.py" , "runserver" , "0.0.0.0:8000" ]
