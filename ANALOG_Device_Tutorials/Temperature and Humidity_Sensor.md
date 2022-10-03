# Temperature & Humidity sensor using Raspberry Pi

Here we use the DHT11 sensor to record the Temperature and Humidity.

## Device 

1. DHT11 Sensor
2. Raspberry PI 4
3. Wires
4. 10k ohm's resistor
5. Breadboad
6. Router


# Operation of accessing data of the analog device

Here the DHT11 sensor senses the tempearature and humidity in the surroundings and the data is processed in the backend(machine) and outputs the temperature in Celsius or Fahrenheit.

# Circuit Diagram










![circuit diagram](https://user-images.githubusercontent.com/112646644/193486886-4569c5a6-7f60-4d9f-9441-4a1a1e74b20c.JPG)









# Connections:

1. Connect pin-1 in DHT11 is Vcc, we connect it to the 5v pin on the PI.
2. pin-2 is the Signal, we connect it to the GPIO for output.
3. pin-4 is the ground connect it to the ground on the PI.

# Installation



## Installing Git-core

Install the git by entering the below command:

              sudo apt-get install git-core
              
              
 We update the upgrade the PI using these commands:
 
             sudo apt-get update

             sudo apt-get upgrade
              
 
 Now clone the repository
 
             git clone https://github.com/WiringPi/WiringPi
             
             
             
             




<img width="437" alt="wiring pi" src="https://user-images.githubusercontent.com/112646644/193489625-c629b318-e026-45ee-b40c-bed8c06ae610.png">
         
             
             
             






Now Access the  wiringpi repository 

           cd WiringPi
         
         
         
         
Create the program :

        nano programname.c
        nano t.c
 
 In the program we must change the counter variable form 16 to 50 to get outout.
        
Program: 

                        #include <wiringPi.h>
                        #include <stdio.h>
                        #include <stdlib.h>
                        #include <stdint.h>
                        #define MAXTIMINGS	85
                        #define DHTPIN		7
                        int dht11_dat[5] = { 0, 0, 0, 0, 0 };

                        void read_dht11_dat()
                        {
                            uint8_t laststate	= HIGH;
                         uint8_t counter		= 0;
                         uint8_t j		= 0, i;
                         float	f; 

                         dht11_dat[0] = dht11_dat[1] = dht11_dat[2] = dht11_dat[3] = dht11_dat[4] = 0;

                         pinMode( DHTPIN, OUTPUT );
                         digitalWrite( DHTPIN, LOW );
                         delay( 18 );
                         digitalWrite( DHTPIN, HIGH );
                         delayMicroseconds( 40 );
                         pinMode( DHTPIN, INPUT );

                         for ( i = 0; i < MAXTIMINGS; i++ )
                         {
                          counter = 0;
                          while ( digitalRead( DHTPIN ) == laststate )
                          {
                           counter++;
                           delayMicroseconds( 1 );
                           if ( counter == 255 )
                           {
                            break;
                           }
                          }
                          laststate = digitalRead( DHTPIN );

                          if ( counter == 255 )
                           break;

                          if ( (i >= 4) && (i % 2 == 0) )
                          {
                           dht11_dat[j / 8] <<= 1;
                           if ( counter > 50 )
                            dht11_dat[j / 8] |= 1;
                           j++;
                          }
                         }

                         if ( (j >= 40) &&
                              (dht11_dat[4] == ( (dht11_dat[0] + dht11_dat[1] + dht11_dat[2] + dht11_dat[3]) & 0xFF) ) )
                         {
                          f = dht11_dat[2] * 9. / 5. + 32;
                          printf( "Humidity = %d.%d %% Temperature = %d.%d C (%.1f F)\n",
                           dht11_dat[0], dht11_dat[1], dht11_dat[2], dht11_dat[3], f );
                         }else  {
                          
                         }
                        }

                        int main( void )
                        {
                         printf( "Raspberry Pi wiringPi DHT11 Temperature test program\n" );

                         if ( wiringPiSetup() == -1 )
                          exit( 1 );

                         while ( 1 )
                         {
                          read_dht11_dat();
                          delay( 1000 ); 
                         }

                         return(0);
                        }
                        
  
  
  
  
  
  
  
  
  
  
  
  To execute the program use the following commands:
    
                 gcc -o t t.c -lwiringPi -lwiringPiDev
                 
                 sudo ./t
                 
                 
                 
                 
  
  
  
  
  
  
 <img width="934" alt="Temperature" src="https://user-images.githubusercontent.com/112646644/193491789-4c334980-f177-41fc-9c94-0cbecd556dd3.png">








<img width="899" alt="Temperature 2" src="https://user-images.githubusercontent.com/112646644/193491815-c9d69634-ac23-4733-bcfd-c1828fb8cfdd.png">













Video:











https://user-images.githubusercontent.com/112646644/193492996-138d2094-91e3-4342-b54d-d7e57c75a60c.mp4
