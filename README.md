# Geo data analysist

 This repo create a docker container with jupyter notebook for geo data analysis

## Prerequisites

Install ```docker``` and ```docker-compose```

- Linux

    ```
    sudo apt-get install docker docker-compose
    ```

- MacOS

    ```
    brew install docker docker-compose
    ```

## Install

Clone this repository and go to cloning folder

```
git clone https://github.com/ChesnovAE/jupyter_docker.git && cd jupyter_docker
```

## Usage

1. First of all you need to generate jupyter_notebook_config.py file. And set the password for jupyter notebook.

    - Generate config file

        ```
        cd geo_app && jupyter notebook --generate-config
        ```

    - Run python3 and type following, then enter your password and copy hashed password from output

        ```
        from notebook.auth import passwd; passwd()
        ```
    
    - Add hashed password in jupyter_notebook_config.py

        ```
        echo "c.NotebookApp.password = '<hashed_password>'" >> jupyter_notebook_config.py
        ```

    If you don't want use password for authentification in notebook, just replace 

    ```
    jupyter notebook --ip 0.0.0.0 --no-browser --allow-root --config /geo_app/jupyter_notebook_config.py
    ``` 

    on 

    ```
    jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
    ```

    in ```geo_app/run.sh file```

2. Let's build our amazing image

    - Go in root folder of repository and run

        ```
        docker-compose build
        ```

        You should see that the build was successful
    
    - Now let's up our container in the background

        ```
        docker-compose up -d
        ```
    
    - Let's check that the container has started

        ```
        docker-compose ps
        ```

        You should see something like this:

        ```
                            Name                    Command        State           Ports          
        ----------------------------------------------------------------------------------
        dockerfordatascience_geo_app_1   /bin/bash run.sh   Up      0.0.0.0:8888->8888/tcp 
        ```
    
    - Now you can try to connect to your jupyter notebook. Just type ```localhost:8888``` in your browser and enter your password or token, if you didn't set a password.

        **How to view a token**

        ```
        docker-compose exec geo_app bash
        ```

        ```
        jupyter notebook list
        ```