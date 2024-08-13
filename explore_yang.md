### Install YANG Suite

Can be installed as a docker container, You will need docker, and docker compose to run.

```
git clone git@github.com:CiscoDevNet/yangsuite.git
cd docker
sudo ./start_yang_suite.sh
```

##### Access Docker Install from Web Browser
```
http://localhost OR http://localhost:8443
```
nginx server running inside docker will redirect to 8443 if you try to hit port 80 so either one of them works.

##### Getting Started
There are 2 ways to get started, first method downloads yang repos from device and seccond model uses locally defined models.

1. Connect to Device 
   1. Setup -> Device Profile
   2. Setup -> Yang files and repositories
2. Upload Yang models from your computer, using
   1. Setup -> Yang files and repositories


