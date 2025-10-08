# 9. The Robot's Trail

  ## DESCRIPTION
  A guardian robot patrols the floor, leaving a trail behind as it moves. Follow the path it carves, trace its movements carefully, and uncover the key it leads you to. Only by following the robot’s trail can you reach the door to the next floor.
  Challenge: https://therobotstrail.citadel.cryptonitemit.in
  
  ## WRITEUP
  Inspect the page, look at the source code. It has a robots.txt file. Opening, we get a hint to open /etc/passwd. There we see a web server config. Go there and try log location. See file path address, follow it to get SECRET_LOCATION. There you find flag.txt and get flag in that address.
 >citadel{p4th_tr4v3rs4l_m4st3ry_4ch13v3d} 