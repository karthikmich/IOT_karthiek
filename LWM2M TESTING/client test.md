## CLIENT TEST USING RASPBERRY PI 

I have Used Iperf for running the following tests in the raspberry pi 4 B+ 

                sudo apt-get install iperf

Later on we can use the below command to check the clients connected to the raspberry pi.

                iperf -s
                
Open a Terminal window and type the following :

                sudo iwlist wlan0 scan  and press Enter
                
  we should be getting results like this :
  
  <img width="1440" alt="Screen Shot 2022-09-23 at 5 04 36 PM" src="https://user-images.githubusercontent.com/107719838/192057306-03de471e-9aaa-4691-ab64-9de5ce5a645c.png">
