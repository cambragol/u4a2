---
grand_parent: DISK 2
parent: SAVE
nav_order: 1
---

# SAVE full listing

```
ORG $6000 (actually loaded into $8800)
LEN $01F0


8800    A5 0F       LDA $0F         ; get party size
8802    85 D4       STA $D4         ; set current player to last
8804    20 2D 08    JSR $082D       ; set $FE/$FF vector based on $D4
8807    A0 12       LDY #$12        ; set play status to DEAD
8809    A9 C4       LDA #$C4        ; .
880B    91 FE       STA ($FE),Y     ; .
880D    A0 18       LDY #$18        ; set hit points to 000
880F    A9 00       LDA #$00        ; .
8811    91 FE       STA ($FE),Y     ; .
8813    C8          INY             ; .
8814    91 FE       STA ($FE),Y     ; .
8816    20 45 08    JSR $0845       ; DISPLAY STATS
8819    20 75 08    JSR $0875       ; clear screen?
881C    20 21 08    JSR $0821       ; print

881F    8D 8D C1 CC CC A0 C9 D3 A0 C4 C1 D2 CB AE AE AE 8D 00                   ^M^MALL IS DARK...^M^@

8831    20 D5 89    JSR $89D5       ; wait a few seconds
8834    20 21 08    JSR $0821       ; print

8837    8D C2 F5 F4 A0 F7 E1 E9 F4 AE AE AE 8D 00                               ^MBut wait...^M^@

8845    20 D5 89    JSR $89D5       ; wait a few seconds
8848    20 21 08    JSR $0821       ; print

884B    D7 E8 E5 F2 E5 A0 E1 ED A0 C9 BF AE AE AE 8D 00                         Where am I?..^M^@

885B    20 D5 89    JSR $89D5       ; wait a few seconds
885E    20 21 08    JSR $0821       ; print

8861    C1 ED A0 C9 A0 E4 E5 E1 E4 BF AE AE AE 8D 00                            Am I dead?...^M^@

8870    20 D5 89    JSR $89D5       ; wait a few seconds
8873    20 21 08    JSR $0821       ; print

8876    C1 E6 F4 E5 F2 EC E9 E6 E5 BF AE AE AE 8D 00                            Afterlife?...^M^@

8885    20 D5 89    JSR $89D5       ; wait a few seconds
8888    20 21 08    JSR $0821       ; print

888B    D9 CF D5 A0 C8 C5 C1 D2 BA 8D 00                                        YOU HEAR:^M^@

8896    A9 01       LDA #$01        ; _D4 = 0x01
8898    85 D4       STA $D4         ; .
889A    20 6F 08    JSR $086F       ; print player name?

889D    A9 8D       LDA #$8D        ; '^M'
889F    20 24 08    JSR $0824       ; print character
88A2    20 D5 89    JSR $89D5       ; wait a few seconds
88A5    20 21 08    JSR $0821       ; print

88A8    C9 A0 E6 E5 E5 EC A0 ED EF F4 E9 EF EE AE AE AE 8D 00                   I feel motion...^M^@

88BA    A9 1F       LDA #$1F        ; _0E = 0x1F
88BC    85 0E       STA $0E         ;
88BE    A9 13       LDA #$13        ; _00 = 0x13
88C0    85 00       STA $00         ;
88C2    A9 08       LDA #$08        ; _01 = 0x08
88C4    85 01       STA $01         ;
88C6    A9 56       LDA #$56        ; _08 = 0x56
88C8    85 08       STA $08         ;
88CA    A9 6C       LDA #$6C        ; _09 = 0x6C
88CC    85 09       STA $09         ;
88CE    A9 01       LDA #$01        ; _0A = 0x01
88D0    85 0A       STA $0A         ;
88D2    A9 00       LDA #$00        ; _0B = 0x00
88D4    85 0B       STA $0B         ;
88D6    85 14       STA $14         ; _14 = 0x00
88D8    A9 03       LDA #$03        ;
88DA    20 42 08    JSR $0842       ; request disk switch to disk 3 (TOWN?)
88DD    20 1B 08    JSR $081B       ; print

88E0    84 C2 CC CF C1 C4 A0 CD C1 D0 C0 AC C1 A4 B8 C2 B0 B0 8D 00             ^DBLOAD MAP@,A$8B00^M^@

88F4    A2 00       LDX #$00        ;

;; copy
; 8BXX => E8XX
; 8CXX => E9XX
; 8DXX => EAXX
; 8EXX => EBXX
; 8FXX => EEXX

88F6    BD 00 8B    LDA $8B00,X     ;
88F9    9D 00 E8    STA $E800,X     ;
88FC    BD 00 8C    LDA $8C00,X     ;
88FF    9D 00 E9    STA $E900,X     ;
8902    BD 00 8D    LDA $8D00,X     ;
8905    9D 00 EA    STA $EA00,X     ;
8908    BD 00 8E    LDA $8E00,X     ;
890B    9D 00 EB    STA $EB00,X     ;
890E    BD 00 8F    LDA $8F00,X     ;
8911    9D 00 EE    STA $EE00,X     ;
8914    E8          INX             ;
8915    D0 DF       BNE $88F6       ; loop back over all values of X

;; @@@

8917    A9 02       LDA #$02        ; _0B = 0x02
8919    85 0B       STA $0B         ; .
891B    20 4B 08    JSR $084B       ; @@@

891E    20 21 08    JSR $0821       ; print

8921    8D 8D CC CF D2 C4 A0 C2 D2 C9 D4 C9 D3 C8 8D                            ^M^MLORD BRITISH^M
8930    D3 C1 D9 D3 BA A0 C9 A0 C8 C1 D6 C5 8D                                  SAYS: I HAVE^M
893D    D0 D5 CC CC C5 C4 A0 D4 C8 D9 8D                                        PULLED THY^M
8948    D3 D0 C9 D2 C9 D4 A0 C1 CE C4 A0 D3 CF CD C5 8D                         SPIRIT AND SOME^M
8958    D0 CF D3 D3 C5 D3 D3 C9 CF CE D3 A0 C6 D2 CF CD 8D                      POSSESSIONS FROM^M
8969    D4 C8 C5 A0 D6 CF C9 C4 AE A0 C2 C5 8D                                  THE VOID. BE^M
8976    CD CF D2 C5 A0 C3 C1 D2 C5 C6 D5 CC A0 C9 CE 8D                         MORE CAREFUL IN^M
8986    D4 C8 C5 A0 C6 D5 D4 D5 D2 C5 A1 8D 00                                  THE FUTURE!^M^@

;; set all players to 'G' and max hit points

8993    A5 0F       LDA $0F         ; get party size
8995    85 D4       STA $D4         ; select last player

8997    20 2D 08    JSR $082D       ; set $FE/$FF vector based on $D4
899A    A0 12       LDY #$12        ; set player status to 'G'
899C    A9 C7       LDA #$C7        ; .
899E    91 FE       STA ($FE),Y     ; .
89A0    A0 1A       LDY #$1A        ; set hit points to max
89A2    B1 FE       LDA ($FE),Y     ; .
89A4    A0 18       LDY #$18        ; .
89A6    91 FE       STA ($FE),Y     ; .
89A8    A0 1B       LDY #$1B        ; .
89AA    B1 FE       LDA ($FE),Y     ; .
89AC    A0 19       LDY #$19        ; .
89AE    91 FE       STA ($FE),Y     ; .
89B0    C6 D4       DEC $D4         ; next player
89B2    D0 E3       BNE $8997       ; loop back if not done

;; set ED11, ED14, ED18-ED1F and ED20-ED2F to 0x00
;; set ED10 and ED13 to 0x02

; set ED2X to 0x00

89B4    A9 00       LDA #$00        ; .
89B6    A2 0F       LDX #$0F        ; .
89B8    9D 20 ED    STA $ED20,X     ; .
89BB    CA          DEX             ; .
89BC    D0 FA       BNE $89B8       ; .

; set ED18-ED1F to 0x00

89BE    A2 07       LDX #$07        ; .
89C0    9D 18 ED    STA $ED18,X     ; .
89C3    CA          DEX             ; .
89C4    D0 FA       BNE $89C0       ; .

; set ED11 and ED14 to 0x00
; set ED10 and ED13 to 0x02

89C6    8D 11 ED    STA $ED11       ; .
89C9    8D 14 ED    STA $ED14       ; .
89CC    A9 02       LDA #$02        ; .
89CE    8D 10 ED    STA $ED10       ; .
89D1    8D 13 ED    STA $ED13       ; .

89D4    60          RTS             ; return

;; wait a few seconds

89D5    A2 0A       LDX #$0A        ;

89D7    A0 FF       LDY #$FF        ;

89D9    A9 FF       LDA #$FF        ;

89DB    38          SEC             ;
89DC    E9 01       SBC #$01        ;
89DE    D0 FB       BNE $89DB       ;
89E0    88          DEY             ;
89E1    D0 F6       BNE $89D9       ;
89E3    CA          DEX             ;
89E4    D0 F1       BNE $89D7       ;

89E6    60          RTS             ;
```