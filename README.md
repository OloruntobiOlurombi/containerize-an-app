# Topic: Containerize An App
> Containers are a powerful mechanism to reuse code from experts. Test your knowledge of the power of containers in the following project by building a container and containerizing an app from scratch!

#### Prerequisites:
- You should have a Cloud9 environment running already in a separate browser tab.

#### Project Structure

<img width="240" alt="Screen Shot 2022-08-21 at 1 59 45 PM" src="https://user-images.githubusercontent.com/40290711/185810733-e41e4db4-6458-4178-9d91-0f2209717783.png">

#### Steps
Let go !!!

##### Step 1: Create a Dockerfile
> Create an empty Dockerfile using the touch command.

> Use the FROM command and reference the latest version of Python here.

> Include the "Hello World" Flask example as an app within your container.

> Copy any relevant directories and libraries in the Dockerfile.

> Make sure any relevant requirements are installed in the Dockerfile.

> Expose the port from the Flask example oin the Dockerfile - make sure you check which one is used by the example!

> Have your Dockerfile run the relevant commands for your app.

```
touch Dockerfile
```

```
FROM python:3.7.3-stretch

WORKDIR /app 

COPY . app.py /app/

# Install packages from requirements.txt 
# hadolint ignore=DL3013
RUN pip install --upgrade pip &&\
    pip install --trusted-host pypi.python.org -r requirements.txt 

# Expose port 80
EXPOSE 8000 

# Run app.py at container launch 
CMD ["python", "app.py"]
```

##### Step 2: Create a python-app

> Create a python file with the following code:

```
# save this as app.py
from flask import Flask, request
from markupsafe import escape 

app = Flask(__name__)

@app.route('/')
def hello():
    name = request.args.get("name", "World")
    return f'Hello, {escape(name)}!'
```    

##### Step 3: Build the container

> Build your container

```
docker build -t my-python-app .
```

<img width="1167" alt="01" src="https://user-images.githubusercontent.com/40290711/185811522-2d1d7a25-e9a6-4166-a6c1-e128a69f0463.png">

#### Step 4: Run the container

> Run the container, opening up a bash shell

<img width="667" alt="Screen Shot 2022-08-21 at 2 32 19 PM" src="https://user-images.githubusercontent.com/40290711/185811804-90f1f4cc-9a94-4fce-a7f2-0892d3644f0d.png">

# The End

