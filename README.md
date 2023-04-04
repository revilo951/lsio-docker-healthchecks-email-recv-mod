# Archived
This functionailty is now built into the container

# lsio docker healthchecks email recv mod
Mod to enable the smtpd email monitor in the [linuxserver.io healthchecks container](https://hub.docker.com/r/linuxserver/healthchecks)

You need to start the container first without this mod, so that the config files you need to modify are generated.

* Stop the running container
* Create the file 90-smtpd (copy the file contents from the one in this repo, or download it from here), somewhere you can map it into the container
* Use a volume to map the file in to this location: `/location/of/file/90-smtpd:/etc/cont-init.d/90-smtpd` in your docker run or docker-compose
* Edit the local_settings.py file that is in the /config directory, and add this line at the bottom, modifying to suit your setup/domain: `PING_EMAIL_DOMAIN = "your.domain.com"`
* Map the SMTP port 2525:2525 in your docker run or docker-compose

Start the container again. you should be able to send email to the container, using the IP/hostname of the container and port 2525 as the mailserver.
