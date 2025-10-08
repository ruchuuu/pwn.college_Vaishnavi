# 16. The Ripper

  ## DESCRIPTION
  The guardian of this floor steps from the shadows. Known only as Jack the Ripper, he watches you carefully. He proclaims himself merciful and hands you a word list to help. He asks you to find the passcode hidden in the file. The word list is your only aid. Only by combining the two correctly, can you uncover the key and move on to the next floor.
  Flag format: citadel{password}

  ## WRITEUP
  Find the hash encrypted format- bcrypt from online site. Can be decrypted using John Ripper decrypt (john command) on the terminal to get the password.
 >citadel{fake_flag_4_fake_pl4y3rs}