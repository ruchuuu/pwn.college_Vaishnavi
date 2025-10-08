# 15. Echoes and Pings

  ## DESCRIPTION
  Allegedly, the message contained an image that predicted the rise of the Citadel. Your task is to uncover what was sent and decode the communication to extract the passcode that will unlock the next floor.

  ## WRITEUP
  Read the .pcap file online. See 2 ICMP end packets. 1st ICMP gives the signature bytes of jpg file- ff d8 ff e0. 2nd ICMP gives bytes of jpg- ff d9. Extract ICMP data of the packets as a jpg file. Use Python and Scapy code to extract the data into jpg. The image has the file.
 >citadel{1_r34lly_w4nt_t0_st4y_4t_y0ur_h0us3}