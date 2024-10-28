# About this Repository
This repository contains shell scripts designed to automate the manual process detailed in the [Oracle 23c Free Docker, APEX & ORDS – all in one simple guide](https://pretius.com/blog/oracle-apex-docker-ords/) for installing the latest versions of:

- Oracle APEX 
- Oracle REST Data Services (ORDS)

These scripts are intended for use with the Official Oracle 23c Image, available [from the Oracle Container Registry](https://container-registry.oracle.com/).


# Instructions
The steps to use the script can be found on the [Single Step Oracle 23c DB + APEX Docker Container](https://mattmulvaney.hashnode.dev/single-step-oracle-23c-db-apex-docker-container) blog.

# Addtional Software Installed

- Sudo
- Nano
- OpenJDK Java 17

# Contributions
Contributions to this repository are encouraged

1. docker create -it --name 23cfree -p 8521:1521 -p 8500:5500 -p 8023:8080 -p 9043:8443 -p 9922:22 -e ORACLE_PWD=E container-registry.oracle.com/database/free:latest
2. curl -o unattended_apex_install_23c.sh https://raw.githubusercontent.com/Pretius/pretius-23cfree-unattended-apex-installer/main/src/unattended_apex_install_23c.sh
3. curl -o 00_start_apex_ords_installer.sh https://raw.githubusercontent.com/Pretius/pretius-23cfree-unattended-apex-installer/main/src/00_start_apex_ords_installer.sh
4. docker cp unattended_apex_install_23c.sh 23cfree:/home/oracle
5. docker cp 00_start_apex_ords_installer.sh 23cfree:/opt/oracle/scripts/startup
6. docker start 23cfree


7. docker exec -it 23cfree /bin/bash
8. tail -f /home/oracle/unattended_apex_install_23c.log
