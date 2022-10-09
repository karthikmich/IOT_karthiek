# Install software to build ESP32 code


## Instructions



1. Clone Anjay-esp32-client repo to raspberry pi


        cd projects

        git clone --recurse-submodules --remote-submodules https://github.com/pschragger/Anjay-esp32-client

should take less then a minute

Install build tools for ESP-IDF

       sudo apt-get install git wget flex bison gperf python3 python3-pip python3-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-        util libusb-1
 
 
                        mkdir -p ~/esp
                        cd ~/esp
                        git clone -b v4.4 --recursive https://github.com/espressif/esp-idf.git
                        
  cd ~/esp/esp-idf
               ./install.sh all
               
               
 Setting up Environment Variables 
 
                . ~/esp/esp-idf/export.sh
                
                cd ~/esp
                cp   -r $IDF_PATH/examples/get-started/hello_world .
                
                 ~/esp/esp-idf/export.sh
              
              cd $IDF_PATH/examples/get-started/hello_world 
              idf.py set-target esp32
              idf.py fullclean
              idf.py menuconfig
              

               idf.py build
               
               find the usb that the esp is connected to
               
               by using lusb
               
               idf.py -p /dev/ttyUSB0 monitor
             
                  . ~/esp/esp-idf/export.sh
                   cd ~/esp
                   cp   -r $IDF_PATH/examples/get-started/blink .
                   
                   
                    ~/esp/esp-idf/export.sh
                    cd $IDF_PATH/examples/get-started/blink 
                    idf.py set-target esp32
                    idf.py fullclean
                    idf.py menuconfig
                    
                    
                    
                cd $IDF_PATH/examples/get-started/blink idf.py build  
                
                cd ~/esp/esp-idf/examples/get-started/blink/main
                
                nano blink_example_main.c
                
  
                   d ~/esp/esp-idf/examples/get-started/blink


         

1. navigate to the "Example Configuration" and hit enter
2. . there are two settings Blink GPIO number and Blink Perion in ms
3. change the blink period in ms to 5 seconds ( 5000 ) 
4. save the results to the sdkconfig (S then Q )


 <img width="960" alt="make -j" src="https://user-images.githubusercontent.com/112646644/194747675-ce05c9e2-1f41-478b-91a7-df7e585b8122.png">
         
         
  <img width="960" alt="ready to flash" src="https://user-images.githubusercontent.com/112646644/194747672-091758a3-1d0e-4c27-b5d6-eda900a59d38.png">
  
  
  <img width="960" alt="hello world" src="https://user-images.githubusercontent.com/112646644/194747670-9379e3b4-6273-4c68-9bca-1b7e0323f221.png">
  
  
 


       
 
