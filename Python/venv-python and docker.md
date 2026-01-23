#vnev
flask run >>>>>>>>> for run flask
venv\\Scripts\\activate >>>>> for run  the python in venv formate  (note while copying the code, before use it have to delete the one of the slash"\\")

**gitbash**
`source venv/Scripts/activate` >>>>>>>to activate the venv in Gitbash

docker build --tag rest_api . >>>>>>>>>>>to create the docker image
docker run -p 5005:5000 rest_api >>>>>>>run the docker image 
docker run -dp 5005:5000 rest_api  >>>>>>run the docker image with the container
docker compose up --build --force-recreate --no-deps web >>>>> for rebuild the docker compose and images.
docker compose up >>>>>>>>>to up the compose file

**Build and run** >>>>docker build and run
docker build -t flask-sample-app .
docker run -p 5000:5000 flask-sample-app

**(code)-dockerfile** >>>>>>>>basic run script for the docker file
FROM python:3.9-slim 
WORKDIR /app 
COPY . /app 
RUN pip install --no-cache-dir -r requirements.txt 
EXPOSE 5000 
ENV FLASK_APP=app.py 
CMD ["flask", "run", "--host=0.0.0.0"]