# BonkeyWonkers Questions

## Step 1

+ Run the Terraform configuration in the directory to create an initial `Dockerfile`. 
+ Run the Dockerfile and ensure it works.

## Step 2

+ Update the Terraform template(`Dockerfile.tpl`) file so that the resulting `Dockerfile` also runs the below commands inside the image as part of the run statement.
+ This must be completed using something other than a simple string variable.

  ```
  whoami
  pwd
  ls -ltra
  ```

+ Run `Terraform` again 
  + Expected contents of resulting `Dockerfile`:

    ```
    FROM dahicks/sample:latest as build
    SHELL ["/bin/bash", "-o", "pipefail", "-c"]
    COPY helloworld.py /app/main.py

    RUN cd /app && \
      whoami && \
      pwd && \
      ls -ltra && \
      chmod +x /app/main.py && \
     pip install Flask-RESTful Flask

    ENTRYPOINT ["python3", "/app/main.py"]
    ```

## Step 3

Build a container:
  + Using the newly created Dockerfile, build a container named `hello`.

Run the docker app:
  + Interactively run the container named `hello`.
    + Using the entrypoint flag `--entrypoint '/bin/bash'` to interactively login to the terminal of the container.
      + You should see something like
      ```shell
        root@c0700134dc42:/exercises#
      ```
   

## Step 4

+ Run docker compose and fix any errors you encounter.
+ Curl the `/hello` endpoint on both containers.
  + output should look like follows

    ```shell
    {
      "data": "Hello World"
    }
    ```

