# NAMafiA Sever


NAMafiA is hosted in AWS and uses the following services:

- STMP Mail Service
- Route 53
- S3
- EC2 Instances

It currently has a 8gig limit which will need to be increased as time goes on.  SMTP mail limit is 5000 a day.  

For hosting, the domain is through namecheap and the routing is done via AWS Route 53.  

## Docker

The forum leverages the build at docker/discourse
  - [docker/discourse](https://github.com/discourse/discourse_docker)

You will find the code in `/var/discourse`

### Custom Docker Changes
To make changes docker container we have really only one way and that is to edit the .yml discourse_docker uses.  On the first launch
```
./launcher build app
```
It will generate a app.yml file in the containers subfolder

There in the app.yml file you can being to alter the discourse forum settings.  This is where we can add plugins and tweak server settings, such as email.

To have any of these changes take place you need to run the command
```
./launcher rebuild app
```
Where launcher.sh is the file being excuted the command is reubild and app is the name of our .yml file.  Since we built it that way.

### Plugins
List of installed plugins:
- TODO

## Backups
Backups are taken on a weekly basis and are stored in an S3 bucket
namafia/backups.
