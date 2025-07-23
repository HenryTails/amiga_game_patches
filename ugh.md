
## Ugh! (Ego Software)

```
ROM name="(sps396)ugh.ipf" size="1049612" crc="2700fd88" sha1="b807e9450a040eaecfd7f333a5f86d10fb5347ef"
```

Tested under Amiga 500 (WinUAE, KS 1.3, 512 KB Chip, 512 KB Slow).

### Unlimited lives

Original code:

```
00c1549a 50f9 00c2 b8a4           st.b $00c2b8a4 [ff] (T)
00c154a0 5339 00c2 b894           subq.b #$01,$00c2b894 [06]
00c154a6 6600 0020                bne.w #$0020 == $00c154c8 (T)
```

Modified code:

```
00c1549a 50f9 00c2 b8a4           st.b $00c2b8a4 [ff] (T)
00c154a0 4a39 00c2 b894           tst.b $00c2b894 [06]
00c154a6 6600 0020                bne.w #$0020 == $00c154c8 (T)
```

### Unlimited energy

Original code:

```
00c151e2 536b 0008                subq.w #$01,(a3,$0008) == $00c25824 [0000]
00c151e6 5379 00c2 b896           subq.w #$01,$00c2b896 [294f]
00c151ec 4bf9 00c2 5f70           lea.l $00c25f70,a5
```

```
00c1528e 526b 000a                addq.w #$01,(a3,$000a) == $00c25826 [001a]
00c15292 5579 00c2 b896           subq.w #$02,$00c2b896 [294d]
00c15298 6000 0006                bra.w #$0006 == $00c152a0 (T)
```

```
00c152de 197c 0028 0004           move.b #$28,(a4,$0004) == $00c247ec [28]
00c152e4 5779 00c2 b896           subq.w #$03,$00c2b896 [294a]
00c152ea 6000 0034                bra.w #$0034 == $00c15320 (T)
```

Modified code:

```
00c151e2 536b 0008                subq.w #$01,(a3,$0008) == $00c25824 [0000]
00c151e6 4e71                     nop
00c151e8 4e71                     nop
00c151ea 4e71                     nop
00c151ec 4bf9 00c2 5f70           lea.l $00c25f70,a5
```

```
00c1528e 526b 000a                addq.w #$01,(a3,$000a) == $00c25826 [001a]
00c15292 4e71                     nop
00c15294 4e71                     nop
00c15296 4e71                     nop
00c15298 6000 0006                bra.w #$0006 == $00c152a0 (T)
```

```
00c152de 197c 0028 0004           move.b #$28,(a4,$0004) == $00c247ec [28]
00c152e4 4e71                     nop
00c152e6 4e71                     nop
00c152e8 4e71                     nop
00c152ea 6000 0034                bra.w #$0034 == $00c15320 (T)
```

### Disable pterodactyl

Original code:

```
00c16406 4e75                     rts  == $00c163c8
00c16408 536a 0010                subq.w #$01,(a2,$0010) == $00c26448 [0172]
00c1640c 4e75                     rts  == $00c163c8
```

Modified code:

```
00c16406 4e75                     rts  == $00c163c8
00c16408 4e71                     nop
00c1640a 4e71                     nop
00c1640c 4e75                     rts  == $00c163c8
```

### Invincible tree

Original code:

```
00c16916 2854                     movea.l (a4) [00c2674c],a4
00c16918 58aa 0016                addq.l #$04,(a2,$0016) == $00c26434 [00c2c744]
00c1691c 342b 0008                move.w (a3,$0008) == $00c25714 [0000],d2
```

Modified code:

```
00c16916 2854                     movea.l (a4) [00c2674c],a4
00c16918 4e71                     nop
00c1691a 4e71                     nop
00c1691c 342b 0008                move.w (a3,$0008) == $00c25714 [0000],d2
```

### Only one mission per level

Original code:

```
00c16cce 536c 0010                subq.w #$01,(a4,$0010) == $00c2bc74 [0002]
00c16cd2 6600 0014                bne.w #$0014 == $00c16ce8 (T)
00c16cd6 50f9 00c2 05b2           st.b $00c205b2 [00] (T)
```

Modified code:

```
00c16cce 536c 0010                subq.w #$01,(a4,$0010) == $00c2bc74 [0002]
00c16cd2 4e71                     nop
00c16cd4 4e71                     nop
00c16cd6 50f9 00c2 05b2           st.b $00c205b2 [00] (T)
```

### Triceratops ignores you

Original code:

```
00c165a6 4a80                     tst.l d0
00c165a8 6700 000e                beq.w #$000e == $00c165b8 (F)
00c165ac 2540 0004                move.l d0,(a2,$0004) == $00c2643c [00c25f36]
```

Modified code:

```
00c165a6 4a80                     tst.l d0
00c165a8 6000 000e                bra.w #$000e == $00c165b8 (T)
00c165ac 2540 0004                move.l d0,(a2,$0004) == $00c2643c [00c25f36]
```

### Disable water level rise

Original code:

```
00c177ce 3014                     move.w (a4) [17aa],d0
00c177d0 d06c 0018                add.w (a4,$0018) == $00c25f88 [ffff],d0
00c177d4 6f00 0008                ble.w #$0008 == $00c177de (F)
```

Modified code:

```
00c177ce 3014                     move.w (a4) [0000],d0
00c177d0 4e71                     nop
00c177d2 4e71                     nop
00c177d4 6f00 0008                ble.w #$0008 == $00c177de (T)
```

### Indestructible vehicles

#### Upper hit box

Original code:

```
00c174c8 b041                     cmp.w d1,d0
00c174ca 6e00 00b6                bgt.w #$00b6 == $00c17582 (F)
00c174ce e0ea 000a                asr.w (a2,$000a) == $00c26b62 [3030]
```

Modified code:

```
00c174c8 b041                     cmp.w d1,d0
00c174ca 4e71                     nop
00c174cc 4e71                     nop
00c174ce e0ea 000a                asr.w (a2,$000a) == $00c25aa8 [0000]
```

#### Bottom hit box

Original code:

```
00c15384 0c6b 0050 000a           cmp.w #$0050,(a3,$000a) == $00c25826 [0000]
00c1538a 6f00 000c                ble.w #$000c == $00c15398 (T)
00c1538e 157c 0001 0012           move.b #$01,(a2,$0012) == $00c25f48 [00]
```

Modified code:

```
00c15384 0c6b 0050 000a           cmp.w #$0050,(a3,$000a) == $00c25826 [0000]
00c1538a 6000 000c                bra.w #$000c == $00c15398 (T)
00c1538e 157c 0001 0012           move.b #$01,(a2,$0012) == $00c25f48 [00]
```

#### Right hit box

Original code:

```
00c17460 b26a 0008                cmp.w (a2,$0008) == $00c25f3e [0000],d1
00c17464 6f00 011c                ble.w #$011c == $00c17582 (F)
00c17468 446a 0008                neg.w (a2,$0008) == $00c25f3e [0000]
```

Modified code:

```
00c17460 b26a 0008                cmp.w (a2,$0008) == $00c2136e [0000],d1
00c17464 4e71                     nop
00c17466 4e71                     nop
00c17468 446a 0008                neg.w (a2,$0008) == $00c2136e [0000]
```

#### Left hit box

Original code:

```
00c17420 b26a 0008                cmp.w (a2,$0008) == $00c25824 [001e],d1
00c17424 6f00 015c                ble.w #$015c == $00c17582 (F)
00c17428 e0ea 0008                asr.w (a2,$0008) == $00c25824 [001e]
```

Modified code:

```
00c17420 b26a 0008                cmp.w (a2,$0008) == $00c25aa6 [0004],d1
00c17424 4e71                     nop
00c17426 4e71                     nop
00c17428 e0ea 0008                asr.w (a2,$0008) == $00c25aa6 [0004]
```

#### Four corners hit box

Original code:

```
00c17572 b041                     cmp.w d1,d0
00c17574 6e00 000c                bgt.w #$000c == $00c17582 (F)
00c17578 e0ea 0008                asr.w (a2,$0008) == $00c25824 [ffef]
```

Modified code:

```
00c17572 b041                     cmp.w d1,d0
00c17574 4e71                     nop
00c17576 4e71                     nop
00c17578 e0ea 0008                asr.w (a2,$0008) == $00c25824 [ffef]
```

### Disable throwing people off the ledges

Original code:

```
00c15410 b06c 0006                cmp.w (a4,$0006) == $00c256ce [0e00],d0
00c15414 6f00 0020                ble.w #$0020 == $00c15436 (F)
00c15418 254e 001c                move.l a6,(a2,$001c) == $00c25fa8 [00c25f36]
```

Modified code:

```
00c15410 b06c 0006                cmp.w (a4,$0006) == $00c256ce [0e00],d0
00c15414 6000 0020                bra.w #$0020 == $00c15436 (T)
00c15418 254e 001c                move.l a6,(a2,$001c) == $00c25fa8 [00c25f36]
```

### Almost everyone likes swimming

Original code:

```
00c15e3a 4e75                     rts  == $00c1581e
00c15e3c 536a 0014                subq.w #$01,(a2,$0014) == $00c25fa0 [010e]
00c15e40 4e75                     rts  == $00c1581e
```

Modified code:

```
00c15e3a 4e75                     rts  == $00c1581e
00c15e3c 4e71                     nop
00c15e3e 4e71                     nop
00c15e40 4e75                     rts  == $00c1581e
```
