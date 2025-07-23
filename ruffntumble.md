
## Ruff'n'Tumble (Renegade)

```
RuffNTumble_v2.8_0199.lha
sha1=6b4012594cd5ae39153f0389772e5bdd90700044
RuffNTumble_v2.8_512k_0199.lha
sha1=4b4153127383e5f9983ceb00271fac3a065923c3
```

Tested under Amiga 1200 + WHDLoad (WinUAE, KS 3.1, 2 MB Chip, 4 MB Fast).

### Unlimited lives

Original code:

```
005d0eb0 6604                     bne.b #$04 == $005d0eb6 (F)
005d0eb2 5338 3e6e                subq.b #$01,$3e6e.w [00]
005d0eb6 6b0c                     bmi.b #$0c == $005d0ec4 (F)
```

Modified code:

```
005d0eb0 6604                     bne.b #$04 == $005d0eb6 (F)
005d0eb2 4a38 3e6e                tst.b $3e6e.w [01]
005d0eb6 6b0c                     bmi.b #$0c == $005d0ec4 (F)
```

### Unlimited energy

Original code:

```
005d07e4 6742                     beq.b #$42 == $005d0828 (T)
005d07e6 5378 3e50                subq.w #$01,$3e50.w [0000]
005d07ea 4a78 3e50                tst.w $3e50.w [0000]
```

Modified code:

```
005d07e4 6742                     beq.b #$42 == $005d0828 (T)
005d07e6 4e71                     nop
005d07e8 4e71                     nop
005d07ea 4a78 3e50                tst.w $3e50.w [0000]
```

### All marbles collected

Original code:

```
005ce23e 43f1 0000                lea.l (a1,d0.w,$00) == $005824f2,a1
005ce242 31e9 0078 3e44           move.w (a1,$0078) == $005824ea [000a],$3e44.w [000a]
005ce248 31e9 007a 3e46           move.w (a1,$007a) == $005824ec [000a],$3e46.w [0000]
005ce24e 31e9 007c 3e48           move.w (a1,$007c) == $005824ee [000a],$3e48.w [0000]
005ce254 6100 06b6                bsr.w #$06b6 == $005ce90c
```

Modified code:

```
005ce23e 43f1 0000                lea.l (a1,d0.w,$00) == $005824f2,a1
005ce242 4278 3e44                clr.w $3e44.w [000a]
005ce246 4278 3e46                clr.w $3e46.w [0000]
005ce24a 4278 3e48                clr.w $3e48.w [0000]
005ce24e 4e71                     nop
005ce250 4e71                     nop
005ce252 4e71                     nop
005ce254 6100 06b6                bsr.w #$06b6 == $005ce90c
```

### Pickup (P) fully refills special weapon

Original code:

```
005d185e 6716                     beq.b #$16 == $005d1876 (F)
005d1860 0678 0080 3e3a           add.w #$0080,$3e3a.w [022e]
005d1866 0c78 0300 3e3a           cmp.w #$0300,$3e3a.w [022e]
```

Modified code:

```
005d185e 6716                     beq.b #$16 == $005d1876 (F)
005d1860 0678 0300 3e3a           add.w #$0300,$3e3a.w [022e]
005d1866 0c78 0300 3e3a           cmp.w #$0300,$3e3a.w [022e]
```

### Unlimited regular ammo

Original code:

```
005d1824 3038 3e32                move.w $3e32.w [0180],d0
005d1828 5940                     subq.w #$04,d0
005d182a 6a02                     bpl.b #$02 == $005d182e (T)
005d182c 7000                     moveq #$00,d0
```

Modified code:

```
005d1824 3038 3e32                move.w $3e32.w [0180],d0
005d1828 4e71                     nop
005d182a 6002                     bra.b #$02 == $005d182e (T)
005d182c 7000                     moveq #$00,d0
```

### Unlimited special ammo

Original code:

```
005d17ec 3038 3e3a                move.w $3e3a.w [02db],d0
005d17f0 5340                     subq.w #$01,d0
005d17f2 31c0 3e3a                move.w d0,$3e3a.w [02db]
```

Modified code:

```
005d17ec 3038 3e3a                move.w $3e3a.w [02db],d0
005d17f0 4e71                     nop
005d17f2 31c0 3e3a                move.w d0,$3e3a.w [02db]
```

### Disable enemy collisions

Original code:

```
005d0884 4a2e 00f7                tst.b (a6,$00f7) == $005d2acf [00]
005d0888 6606                     bne.b #$06 == $005d0890 (F)
005d088a 4a47                     tst.w d7
```

Modified code:

```
005d0884 4a2e 00f7                tst.b (a6,$00f7) == $005d2acf [00]
005d0888 6006                     bra.b #$06 == $005d0890 (T)
005d088a 4a47                     tst.w d7
```

### Universal key

Original code:

```
005d14be 4a78 3e3c                tst.w $3e3c.w [0000]
005d14c2 67ba                     beq.b #$ba == $005d147e (T)
005d14c4 5378 3e3c                subq.w #$01,$3e3c.w [0000]
005d14c8 0251 83ff                and.w #$83ff,(a1) [642a]
005d14cc 60d2                     bra.b #$d2 == $005d14a0 (T)
005d14ce 4a78 3e3e                tst.w $3e3e.w [0000]
005d14d2 67aa                     beq.b #$aa == $005d147e (T)
005d14d4 5378 3e3e                subq.w #$01,$3e3e.w [0000]
005d14d8 0251 83ff                and.w #$83ff,(a1) [642a]
005d14dc 60c2                     bra.b #$c2 == $005d14a0 (T)
```

Modified code:

```
005d14be 4a78 3e3c                tst.w $3e3c.w [0000]
005d14c2 4e71                     nop
005d14c4 4e71                     nop
005d14c6 4e71                     nop
005d14c8 0251 83ff                and.w #$83ff,(a1) [642a]
005d14cc 60d2                     bra.b #$d2 == $005d14a0 (T)
005d14ce 4a78 3e3e                tst.w $3e3e.w [0000]
005d14d2 4e71                     nop
005d14d4 4e71                     nop
005d14d6 4e71                     nop
005d14d8 0251 83ff                and.w #$83ff,(a1) [642a]
005d14dc 60c2                     bra.b #$c2 == $005d14a0 (T)
```
