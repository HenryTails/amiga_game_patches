
## Clik Clak (Idea)

```
Clik Clak (1992)(Idea)[cr SCX].adf
sha1=7ad5c3a9de83bf260dd5a4d07eca824774c40503
```

Tested under Amiga 500 (WinUAE, KS 1.3, 512 KB Chip, 512 KB Slow).

### Unlimited lives

Original code:

```
0000b6b0 4279 0000 e2c8           clr.w $0000e2c8 [0000]
0000b6b6 5379 0000 f28c           subq.w #$01,$0000f28c [0002]
0000b6bc 4279 0000 f28e           clr.w $0000f28e [0000]
```

Modified code:

```
0000b6b0 4279 0000 e2c8           clr.w $0000e2c8 [0000]
0000b6b6 4e71                     nop
0000b6b8 4e71                     nop
0000b6ba 4e71                     nop
0000b6bc 4279 0000 f28e           clr.w $0000f28e [0000]
```

### Unlimited time

Original code:

```
0000d5ae 6c00 0026                bge.w #$0026 == $0000d5d6 (T)
0000d5b2 d0b9 0000 f2ac           add.l $0000f2ac [00000064],d0
0000d5b8 4a79 0000 e2c8           tst.w $0000e2c8 [0000]
```

Modified code:

```
0000d5ae 6c00 0026                bge.w #$0026 == $0000d5d6 (T)
0000d5b2 4e71                     nop
0000d5b4 4e71                     nop
0000d5b6 4e71                     nop
0000d5b8 4a79 0000 e2c8           tst.w $0000e2c8 [0000]
```

### Disable penalty time for locked gears

Original code:

```
0000d5be 6700 0008                beq.w #$0008 == $0000d5c8 (T)
0000d5c2 d0b9 0001 00d0           add.l $000100d0 [00000032],d0
0000d5c8 23c0 0000 f2a8           move.l d0,$0000f2a8 [0000254e]
```

Modified code:

```
0000d5be 6700 0008                beq.w #$0008 == $0000d5c8 (T)
0000d5c2 4e71                     nop
0000d5c4 4e71                     nop
0000d5c6 4e71                     nop
0000d5c8 23c0 0000 f2a8           move.l d0,$0000f2a8 [0000254e]
```

### Unlimited shots

Original code:

```
0000d6d4 4cdf 0201                movem.l (a7)+,d0/a1
0000d6d8 5379 0000 f290           subq.w #$01,$0000f290 [0004]
0000d6de 6100 fa1c                bsr.w #$fa1c == $0000d0fc
```

Modified code:

```
0000d6d4 4cdf 0201                movem.l (a7)+,d0/a1
0000d6d8 4e71                     nop
0000d6da 4e71                     nop
0000d6dc 4e71                     nop
0000d6de 6100 fa1c                bsr.w #$fa1c == $0000d0fc
```

### Unlimited bombs

Original code:

```
0000d754 0270 0040 1000           and.w #$0040,(a0,d1.w,$00) == $0000f7f2 [0040]
0000d75a 5379 0000 f292           subq.w #$01,$0000f292 [0004]
0000d760 48e7 f0e0                movem.l d0-d3/a0-a2,-(a7)
```

Modified code:

```
0000d754 0270 0040 1000           and.w #$0040,(a0,d1.w,$00) == $0000f7f2 [0040]
0000d75a 4e71                     nop
0000d75c 4e71                     nop
0000d75e 4e71                     nop
0000d760 48e7 f0e0                movem.l d0-d3/a0-a2,-(a7)
```

### Unlimited oil

Original code:

```
0000d714 0270 007f 1000           and.w #$007f,(a0,d1.w,$00) == $0000f72c [0072]
0000d71a 5379 0000 f294           subq.w #$01,$0000f294 [0004]
0000d720 6100 f9da                bsr.w #$f9da == $0000d0fc
```

Modified code:

```
0000d714 0270 007f 1000           and.w #$007f,(a0,d1.w,$00) == $0000f72c [0072]
0000d71a 4e71                     nop
0000d71c 4e71                     nop
0000d71e 4e71                     nop
0000d720 6100 f9da                bsr.w #$f9da == $0000d0fc
```

### Freeze enemy logic

Original code:

```
0000e6da 6d00 01a0                blt.w #$01a0 == $0000e87c (F)
0000e6de 5369 0008                subq.w #$01,(a1,$0008) == $000320e8 [0000]
0000e6e2 6e00 0006                bgt.w #$0006 == $0000e6ea (F)
```

Modified code:

```
0000e6da 6d00 01a0                blt.w #$01a0 == $0000e87c (F)
0000e6de 4e71                     nop
0000e6e0 4e71                     nop
0000e6e2 6e00 0006                bgt.w #$0006 == $0000e6ea (F)
```
