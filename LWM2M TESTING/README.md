# LWM2M TESTING USING RASPBERRY PI
Lightweight M2M is an open protocol from the Open Mobile Alliance (OMA) that is designed for addressing the needs of mobile low-power devices with very little compute power. LWM2M is being adopted widely by telecom operators and is emerging as the standard protocol for device management and service enablement.

# STEPS
Logon to Raspbery PI
              
             ssh dietpi@(IPADDR_OF_PI)
Install development environment on RPI
    
                  sudo dietpi-software
search for git ( should be package 17 ) press spacebar to select ( asterick [*] should show tab to ok and press enter navigate to install on dietpi-software menu page press enter and it should show that the software

      - Git: Clone and manage Git repositories locally
Download JDK Software
         sudo dietpi-software
         
         - Java JDK: OpenJDK Development Kit
         
         java --version
Install maven on the rapberry pi
          mkdir download
          
          cd download
          
          wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz
          
          tar xzvf apache-maven-3.8.6-bin.tar.gz
          
          echo 'PATH="${PATH}:~/download/apache-maven-3.8.6/bin"' >>  ~/.bashrc
          
          sudo echo 'JAVA_HOME="/usr/lib/jvm/java-17-openjdk-arm64"' >> ~/.bashrc
          
          nano ~/.bashrc ( To check the contents )
By doing all these steps we can get the maven software

Install Leshan git and build
                 cd
                 mkdir projects
                 cd projects
                 git clone https://github.com/eclipse/leshan.git
Build Leshan
                 cd ~/projects/leshan
                 mvn clean install
Test the Leshan server
                 cd ~/projects/leshan
                 java -jar leshan-server-demo/target/leshan-server-demo-*-SNAPSHOT-jar-with-dependencies.jar &
                 
                 http://{RPI-IP_ADDRESS}:8080
                 
                 
                 java -jar leshan-client-demo/target/leshan-client-demo-*-SNAPSHOT-jar-with-dependencies.jar

