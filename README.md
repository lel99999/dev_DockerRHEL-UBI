# dev_DockerRHEL-UBI
Docker Notes for Using RHEL UBI (Universal Base Images) for RHEL 7 and RHEL 8

#### Docker Search UBI
```
$ docker search registry.access.redhat.com/ubi
```


#### Using UBI SCL Container
[https://access.redhat.com/documentation/en-us/red_hat_software_collections/3/html-single/using_red_hat_software_collections_container_images/index](https://access.redhat.com/documentation/en-us/red_hat_software_collections/3/html-single/using_red_hat_software_collections_container_images/index) <br/>

#### Basic Example
```
# Set base image
FROM registry.redhat.io/rhscl/python-38-rhel7

# Add application sources
ADD --chown=1001:0 app-src .

# Install the dependencies
RUN pip install -U "pip>=19.3.1" && \ 
    pip install -r requirements.txt && \ 
    python manage.py collectstatic --noinput && \ 
    python manage.py migrate

# Run the application
CMD python manage.py runserver 0.0.0.0:8080
```
