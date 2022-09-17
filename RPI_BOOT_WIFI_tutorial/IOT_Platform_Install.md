# Setup steps for the IoT Platform Installation.


SSH to the RPI using dietpi user

ssh dietpi@[PI_IPADDRESS]

You should be seeing these steps after the RPI OS installation :


<img width="1440" alt="review" src="https://user-images.githubusercontent.com/112646644/190835567-dff672f9-7b1f-4d6e-bd61-c282d92c3d85.png">








<img width="1440" alt="Main Menu" src="https://user-images.githubusercontent.com/112646644/190835579-801b1d3f-55a2-495f-97a6-84ead28c9163.png">





Install software on the PI using dietpi-software command
search for mqtt and select 123 MQTT message broker install by hitting the spacebar and selecting ok
search for node-red and select "122 Node-RED: tool for wiring devices, APIs and online services" install by hitting the spacebar and selecting ok
search for postgress and select "194 PostgreSQL: Persistent advanced object-relational database server" install by hitting the spacebar and selecting ok
Move curser to Install and tab to ok
Once you hit enter it should indicate:
DietPi is now ready to install your software choices:
Node-RED: tool for wiring devices, APIs and online services
Mosquitto: MQTT messaging broker
PostgreSQL: Persistent advanced object-relational database server
tab to OK and start the install





<img width="1440" alt="software installation" src="https://user-images.githubusercontent.com/112646644/190835597-9c3ecd9f-a951-4ef4-afd9-45a18979c61c.png">




it will take a while to install ( I measured 11 minutes at home on the wifi)
It should show the all the services restarted
reboot the pi on the command line using reboot command and ssh in again.
Postgres


run on your pi ssh session
      
         sudo su postgres

Create a user with :

         
         createuser pi -P --interactive

When prompted, enter a password (and remember what it is), select n for superuser, and y for the next two questions.

Now connect to Postgres using the shell and create a test database:
psql

        
          create database test;

Exit from the psql shell and again from the Postgres user by pressing Ctrl+D twice, and you'll be logged in as the pi user again. Since you created a Postgres user called pi, you can access the Postgres shell from here with no credentials:
sudo su postgres

           psql test

           create table people (name text, company text);

Now add data

           insert into people values ('Ben Nuttall', 'Raspberry Pi Foundation');

           insert into people values ('Rikki Endsley', 'Red Hat');

test that the data persists:

      
        select * from people;
        
        
The result should be something like this :




<img width="536" alt="sql test output" src="https://user-images.githubusercontent.com/112646644/190835787-c9c9e69a-d16f-4460-8503-aee74463bfba.png">







Need to run plsql on your pi an alter the listen_address settings using:

              sudo su postgres

              psql test





# NODE-RED


Connect to node-red to see that it is running using it RPI Static IPaddr
http://{YOUR_RPI_IPADDRESS}:1880




<img width="1440" alt="Node Red" src="https://user-images.githubusercontent.com/112646644/190835821-158baab9-8707-463e-9544-b3bce3887000.png">







Install node-red-contrib-re-postgres in your ssh command line using:
npm install node-red-contrib-re-postgres

Restart node-red with the command
dietpi-services restart node-red



Go to Manage Pallet and install node-red-contrib-postgresql
Install should note that it is working
pull a postgres node into a flow
click on the node and configure a database instance
Be sure to label it and set Recieve query output? and Return message on error on by enabling checkboxes and save
Pull in a trigger and template node and debug node and wire

trigger->template->Postgres->debug


<img width="1434" alt="FINAL FLOW" src="https://user-images.githubusercontent.com/112646644/190835863-6082764b-1c73-41c6-84f8-7085365698ca.png">











