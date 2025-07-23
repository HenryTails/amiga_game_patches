
## Logical (Rainbow Arts)

```
Log!cal (1991)(Rainbow Arts)[cr RSi].adf
sha1=56874efa68b9b0332aa24f1052ea152aa0d7c057
```

Tested under Amiga 500 (WinUAE, KS 1.3, 512 KB Chip, 512 KB Slow).

### Unlimited lives

Original code:

```
000106ae 6728                     beq.b #$28 == $000106d8 (F)
000106b0 53ad 8a10                subq.l #$01,(a5,-$75f0) == $00c0e0e8 [00000002]
000106b4 202d 8a10                move.l (a5,-$75f0) == $00c0e0e8 [00000002],d0
```

Modified code:

```
000106ae 6728                     beq.b #$28 == $000106d8 (F)
000106b0 4e71                     nop
000106b2 4e71                     nop
000106b4 202d 8a10                move.l (a5,-$75f0) == $00c0e0e8 [00000002],d0
```

### Disable next ball timer

Original code:

```
0001162c 42ad 83dc                clr.l (a5,-$7c24) == $00c0dab4 [00000010]
00011630 53ad 83c4                subq.l #$01,(a5,-$7c3c) == $00c0da9c [00000100]
00011634 53ad 83c4                subq.l #$01,(a5,-$7c3c) == $00c0da9c [00000100]
00011638 7064                     moveq #$64,d0
```

Modified code:

```
0001162c 42ad 83dc                clr.l (a5,-$7c24) == $00c0dab4 [00000001]
00011630 4e71                     nop
00011632 4e71                     nop
00011634 4e71                     nop
00011636 4e71                     nop
00011638 7064                     moveq #$64,d0
```

### Disable level timer

Original code:

```
000105a2 6e2a                     bgt.b #$2a == $000105ce (F)
000105a4 52ad 8378                addq.l #$01,(a5,-$7c88) == $00c0da50 [00000234]
000105a8 42ad 87e0                clr.l (a5,-$7820) == $00c0deb8 [00000000]
```

Modified code:

```
000105a2 6e2a                     bgt.b #$2a == $000105ce (F)
000105a4 4e71                     nop
000105a6 4e71                     nop
000105a8 42ad 87e0                clr.l (a5,-$7820) == $00c0deb8 [00000000]
```
