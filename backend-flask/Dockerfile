FROM python:3.10-slim-buster

# Inside container: Make a new folder inside conainer
WORKDIR /backend-flask

# copy from Outside container (from host os) -> Inside container
COPY requirements.txt requirements.txt

# Inside container
RUN pip3 install -r requirements.txt

# Outside container -> Inside container
#.. means everything in the current directory
#first period . /backend-flask (outside container)
#second period . /backed-flask (inside container)
COPY . .

# set Enviroment Variable (Env Vars)
# inside container and will remain set when the container is running
ENV FLASK_ENV=development

EXPOSE ${PORT}
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]