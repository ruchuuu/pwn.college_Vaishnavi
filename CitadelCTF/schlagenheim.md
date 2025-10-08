# 12. schlagenheim

  ## DESCRIPTION
  The passcode to the next floor is hidden within this piece of music, but it can’t be played, as if the wrong extension has scrambled it. You must take the corrupted file and repair it to reveal the true code that will unlock the door forward.

  ## WRITEUP
  Opened the .wav file but can't because it is not supported by an ordinary player. Also, upon searching the word schlagenheim, we found out that the term was invented by the band black midi. This suggests that the file has to be opened as a midi file with .mid extension. Converted the file to midi but still found the file to be corrupted. M1D1 had to be changed to MThd (header file for midi). Repairing it through online sites or VSCode, we can run it on any midi player and the flag can be seen in the notes.
 >citadel{8lackM1D1wa5c00l}