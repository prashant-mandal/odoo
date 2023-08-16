## What is Odoo?

[Odoo](https://www.odoo.com) is a suite of business management software tools including, for example, CRM, e-commerce, billing, accounting, manufacturing, warehouse, project management, and inventory management.

It is open souce, and is customizable. [Github link](https://github.com/odoo/odoo)

## How to setup odoo on your local system?

With these few easy steps, you can easily run you odoo instance using [docker](https://docs.docker.com/get-started/overview/).<br/>
Here, I will guide you to setup odoo version 16.0 . However you can install any version as the steps are similer.

- Step 1

  - You need to [install docker](https://docs.docker.com/get-docker/) on your local machine.
  - Once installed, got to the terminal and pull the image for v16.0

  ```{r, engine='bash', count_lines}
  docker pull prashant7/odoo:odoo16
  ```

  For other versions of odoo, you can pull the images from my [docker hub](https://hub.docker.com/r/prashant7/odoo)

  - Now, that image is pulled. You need to run the container. For that,
    first create a new folder in your local machine and execute the following command. you can change the "/path/my_local_folder" with path of your folder.

  ```{r, engine='bash', count_lines}
  docker run -it -p 8016:8069 -v "/path/my_local_folder":"mnt/addons" prashant7/odoo:odoo16 bin/bash
  ```

- Step 2

  - Your container is now up and running. The commands executed here will be limited to the container itself.<br/>
    Start the postgres server

  ```{r, engine='bash', count_lines}
  service postgresql start
  ```

  - Start the odoo instance

  ```{r, engine='bash', count_lines}
  /opt/odoo16/odoo/odoo-bin -c /etc/odoo16.conf --logfile=/
  ```

- Step 3
  - Go to your browser and enter [localhost:8016](http://localhost:8016/)
    <br/>syntax: _http://<your_domain_or_IP_address>:port_
    <br/>
    <br/> Your Setup is complete!

## What to-do next?

You can now see a login screen, enter the following credentials:
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; Email: &nbsp; &nbsp; &nbsp;&nbsp;admin
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Password: &nbsp; &nbsp; &nbsp; admin

### Restarting the odoo instance

If you happen to close the conatainer or your system. The next time you want to run the odoo instance, you don't have to go through the hassle of setting up again.
<br/><br/>
Simply follow these steps:

- Start the docker container
  - Open the terminal, run the following command
  ```{r, engine='bash', count_lines}
  docker ps -a
  ```
  - copy the container name or container id
  - Start the container
  ```{r, engine='bash', count_lines}
  docker start <container_name 0r container_id>
  ```
  - Execute the container
  ```{r, engine='bash', count_lines}
  docker exec -it <container_name 0r container_id> bin/bash
  ```
- Follow **Step 2** and **Step 3** mentioned previously.
