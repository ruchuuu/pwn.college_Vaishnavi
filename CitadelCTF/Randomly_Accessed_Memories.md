# 7. Randomly Accessed Memories

  ## DESCRIPTION
  On your ascent to this floor, you hear these fragments being played back  
  clone it, pull it, reset it, stage it,
  commit, push it, fork, rebase it,
  merge it, branch it, tag it, log it,
  add it, stash it, diff, untrack it.  
  You look around and discover a chamber containing a vast archive of Daft Punk’s music, intertwined with cryptic commits left behind by other musicians. They seem ordinary at first glance, but not everything in the history is what it seems.  
  Challenge: https://github.com/evilcryptonite/daft-punk-archive
  ## WRITEUP
  Lyrics being a hint, clone the git in the terminal, and use git log command (git log --oneline --graph --all) to get all the routine updates. Notice the 3 updates where secret chunk is added and removed. Used git show command (git show 79af115)(git show cc8b79a)(git show 50474f3) to see those changes committed and got 3 portions base64 coded. Decode the 3 parts to get the flag.
 >citadel{w3_4r3_up_4ll_n1t3_t0_g1t_lucky}