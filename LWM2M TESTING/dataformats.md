# Data Formats for Transferring Resource Information

###  Four data formats are defined by the LWM2M Enabler in this section. The LWM2M Server MUST support all data formats. The plain text and opaque formats MUST be supported by the LWM2M Client. The LWM2M Client MUST support the TLV data format for Object Instance or multiple-instance Resource requests.


# Plain Text
The plain text format is used for ”Read” and “Write” operations on singular Resources where the value of the Resource is simply represented as an UTF-8 encoded string. This string can contain a character sequence, integer number, decimal number or any other sequence of valid UTF-8 characters as per Appendix A.

                       
                        find / -name example.txt
                        
                        nano example.txt



# Opaque
The opaque format is used for “Read” and “Write” operations on singular Resources where the value of the Resource is an opaque sequence of binary octets. This data format is used for binary Resources such as firmware images or application specific binary formats.

This data format has a Media Type of application/vnd.oma.lwm2m+opaque

 

# TLV
For requests to Object Instance or Resource which supports multiple instances (Resource Instance), the binary TLV (Type-Length-Value) format is used to represent an array of values or a singular value using a compact binary representation, which is easy to process on simple embedded devices. The format has a minimum overhead per value of just 2 bytes and a maximum overhead of 5 bytes depending on the type of Identifier and length of the value. The maximum size of an Object Instance or Resource in this format is 16.7 MB. The format is self-describing, thus a parser can skip TLVs for which the Resource is not known.


                        rameHeaderStructType = struct(... 'sync', {'uint64', 8}, ... % syncPattern in hex is: '02 01 04 03 06 05 08 07'

                     % TLV Type: 06 = Point cloud, 07 = Target object list, 08 = Target index tlvHeaderStruct = struct(... 'type', {'uint32', 4}, ... % TLV object

   ## This is the code snippet that I am currently using:

                         ser = serial.Serial("/dev/ttyACM1", 115200)   

                         while True:

                         received_data = ser.readline()              

                         sys.stdout.write(received_data.encode("hex"))




# JSON

LWM2M Clients supporting the JSON format MUST use the format defined in this section for responses with multiple ressource values. They MAY use the format defined in this section for responses with single value.



                          json-tui example.json 

