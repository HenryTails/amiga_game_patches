
## Logical (Rainbow Arts)

```
Logical_v1.2_CDTV.lha
sha1=d5620e4af3e3644ebf061dc9dcba9088edb37602
```

Tested under Amiga 1200 + WHDLoad (WinUAE, KS 3.1, 2 MB Chip, 4 MB Fast).

### Unlimited lives

Original code:

```
005cb7b2 6728                     beq.b #$28 == $005cb7dc (T)
005cb7b4 53ad 8a32                subq.l #$01,(a5,-$75ce) == $005e8862 [00000000]
005cb7b8 202d 8a32                move.l (a5,-$75ce) == $005e8862 [00000000],d0
```

Modified code:

```
005cb7b2 6728                     beq.b #$28 == $005cb7dc (T)
005cb7b4 4e71                     nop
005cb7b6 4e71                     nop
005cb7b8 202d 8a32                move.l (a5,-$75ce) == $005e8862 [00000000],d0
```

### Disable next ball timer

Original code:

```
005bf218 42ad 83fe                clr.l (a5,-$7c02) == $005dad06 [00000000]
005bf21c 53ad 83e6                subq.l #$01,(a5,-$7c1a) == $005dacee [0000010f]
005bf220 53ad 83e6                subq.l #$01,(a5,-$7c1a) == $005dacee [0000010f]
005bf224 7064                     moveq #$64,d0
```

Modified code:

```
005bf218 42ad 83fe                clr.l (a5,-$7c02) == $005dad06 [00000000]
005bf21c 4e71                     nop
005bf21e 4e71                     nop
005bf220 4e71                     nop
005bf222 4e71                     nop
005bf224 7064                     moveq #$64,d0
```

### Disable level timer

Original code:

```
005be172 6e2a                     bgt.b #$2a == $005be19e (F)
005be174 52ad 839a                addq.l #$01,(a5,-$7c66) == $005daca2 [0000000d]
005be178 42ad 8802                clr.l (a5,-$77fe) == $005db10a [00000032]
```

Modified code:

```
005be172 6e2a                     bgt.b #$2a == $005be19e (F)
005be174 4e71                     nop
005be176 4e71                     nop
005be178 42ad 8802                clr.l (a5,-$77fe) == $005db10a [00000032]
```
