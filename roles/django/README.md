
Author:
Harisha Ameen

Dependencies:
None

Tags:
Debian : when mentioned tasks get executed only on Debian OS family nodes.

Description:
Installs and configures python django framework on Ubuntu OS. The role can install django both on globally as wel as in a virtual environment.

To install django globally, run the below command:
ansible-playbook django.yml

To install it on virtual environment, with a default project created:
ansible-playbook django.yml --extra-vars 'is_virtualenv=true create_project=true'

Variables
pip_pkg: 'python-pip' #python pip package name to install
is_virtualenv: false  #if false, django will not be installed in a virtual environment. By default it is false, can be overriden by command line extra vars argument.
user: django          #Default django installation user
user_home: "/home/{{user}}" #Django installation user home directory
project_name: my_website                         #Default django project name, can be overriden by command line arguments.
project_dir: "{{user_home}}/{{project_name}}"    #Project directory
migrate: true                                    #To bootstrap the database on more recent versions of Django
server_port: 8000                                #django web application listen port
server_ip: localhost                             #django web application listen address

Simple override command line argument example:
ansible-playbook django.yml --extra-vars 'is_virtualenv=true create_project=true server_port=80 server_ip=192.168.0.3'
