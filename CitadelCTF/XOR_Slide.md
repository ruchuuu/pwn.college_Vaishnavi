# 13. XOR Slide

  ## DESCRIPTION
  You realise that a previous climber has set up a puzzle in what was otherwise an empty room, blocking the entrance to the next floor on the ceiling. You must slide the blocks forming the pyramid to create a path above.

  ## WRITEUP
  Given cyphertext(b31113bd631c7207ec9587b32e686c8b6df255d66f4a987adacf6c283875ded5d1633b5f8823fa0b9bbbfab3195f1a51506afd54e03392ae338d872445c9025d88c8d4425a00a9b4478f86acadbd781df6a4194e376c09145a6f9afcbe02d36b5709f74d910edf94552dc4680041d6717fea824718c21385bdfd6176f722100548336d10ead87f01a95c5497dcb6c2) is encrypted with sliding XOR. When ran through the python code given, each ciphertext position xored with respective known wrapper and previous found keystream to recover the plaintext.
 >citadel{pyr4m1d+x0r}