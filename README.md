# README #

eGAR Secrets Yaml devinition and startup/shutdown scripts

### What is this repository for? ###

The secrets yaml file is invoked before any other yaml files are spun up. This loads the secrets which are used by the other APIs for the purpose of database connections, AWS resources and so on.

### How do I get set up? ###

* Create an encoded version of your secret by typing 'echo -n secretword | base64' at the command line.
* Add the encrypted string to the value in the secrets.yaml file
* Load the secrets file before running any pods which require them.
* Reference the secret within the yaml file of the pod. For instance, the lines below are included within the 'environment' definition of the deployment yaml file:

- name: EGAR_LIVE_KEY
- valueFrom:
- secretKeyRef:
- name: egar-notify-secret
- key: egarlivekey

* In the above example, the environment parameter 'EGAR_LIVE_KEY' is assigned the value given for 'egarlivekey' within the secret definition called 'egar-notify-secret'. The environment parameter is made available within the pod and the value is decoded from the base64 encoding.

### Contribution guidelines ###

* Writing tests
* Code review
* Other guidelines

### Who do I talk to? ###

* Repo owner or admin
* Other community or team contact
