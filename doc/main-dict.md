# Main Dictionary.

The Language start with this words defined, in top of this you can define new word until you program is done.

## Stack Manipulation Words
```
DUP 	| a -- a a
DROP 	| a --
OVER 	| a b -- a b a
PICK2 	| a b c -- a b c a
PICK3 	| a b c d -- a b c d a
PICK4 	| a b c d e -- a b c d e a
SWAP 	| a b -- b a
NIP		| a b -- b
ROT 	| a b c -- b c a
2DUP 	| a b -- a b a b
2DROP   | a b --
3DROP   | a b c --
4DROP   | a b c d --
2OVER	| a b c d -- a b c d a b
2SWAP	| a b c d -- c d a b
```

## Control flow construction
```
(	| Start Block
)	| End Block
)(  | Separator Block, see carrefuly, not space between )(

[	| Start anonymous definition
]	| End anonymous definition leave direction on stack
```

## Conditionals
```
0? 	| --		; is 0 the Top of Stack (TOS)
+? 	| --		; TOS positive (or 0)?
-?	| --		; TOS negative ?
1? 	| --		; TOS diferent from 0?
=?	| a b -- a	; a = b ?
<?	| a b -- a	; a < b ?
>?	| a b -- a	; a > b ?
<=?	| a b -- a	; a <= b ?
>=?	| a b -- a	; a >= b ?
<>?	| a b -- a	; a <> b ?
AND?	| a b -- a	; a and b ?
NAND?	| a b -- a	; a nand b ?
```

## Return Stack Manipulation
```
;	| --		R: a -- 	; End Word
>R 	| a --      R: -- a		; Data to Return stack
R> 	| -- a		R: a --		; Return to Data stack
R@	| -- a      R: a -- a	; Get Return Top of Stack

EXEC  	| vector --  ; call to vector
```

## Arithmetic and logic operators
```
AND 	| a b -- c     c = a AND b
OR 		| a b -- c     c = a OR b
XOR 	| a b -- c     c = a XOR b
NOT  	| a b -- c     c = a NOT b
+ 		| a b -- c		c=a+b
- 		| a b -- c		c=a-b
* 		| a b -- c		c=a*b
/ 		| a b -- c		c=a/b
*/ 		| a b c -- d	d=a*b/c		;64 bits intermedial
*>>		| a b c -- d	d=(a*b)>>c	;64 bits intermedial
<</		| a b c -- d	d(a<<c)/b	;64 bits intermedial
/MOD 	| a b -- c d	c=a/b  d=a module b
MOD 	| a b -- c		c=a module b
ABS		| a -- b		b=|a|
CLZ		| a -- b		count leanding zeros
SQRT	| a -- b		square root
NEG 	| a -- b		b=-a
1+ 		| a -- b		b=a+1
4+		| a -- b		b=a+4
1- 		| a -- b		b=a-1
2/ 		| a -- b		b=a/2
2* 		| a -- b		b=a*2
<< 		| a b -- c		c=a<<b
>> 		| a b -- c		b=a>>b (sign)
0>>		| a b -- c		b=a0>>b (zero)
```

## Memory access
```
@ 		| a -- b		b=32(a)
C@ 		| a -- b		b=8 (a)
W@		| a -- b		b=16(a)
!		| v d --		32(d) = v
C!		| v d --		8(d) = v
W! 		| v d --		16(d) = v
+! 		| v d --		32(d)=32(d)+v
C+!		| v d --		8(d)=8(d)+v
W+!  	| v d --		16(d)=16(d)+v
@+		| d -- d+4 v	dword (32bits)
!+		| v d -- d+4
C@+		| d -- d+1 v	byte (8bits)
C!+		| v d -- d+1
W@+		| d -- d+2 v	word (16bits)
W!+		| v d -- d+2
```

## Pointer registers A and B
```
>A		| v --		A=v ; A is a register for use like pointer
A>		| -- v      v=A
A+		| v --		A=A+v
A@		| -- v		v=[A]
A!		| v --		[A]=v
A@+		| -- v		v=[A] A=A+4
A!+		| v --		[A]=v A=A+4

>B		| v --		B=v ; B is a register for use like pointer
B>		| -- v		v=B
B+		| v --		B=B+v
B@		| -- v		v=[B]
B!		| v --		[B]=v
B@+		| -- v		v=[B] B=B+4
B!+		| v --		[B]=v B=B+4
```

## Memory copy and fill
```
MOVE	| de sr cnt --	; Copy CNT dword from SR to DE
MOVE>   | de sr cnt --	; Copy CNT dword from SR to DE (reverse)
FILL	| v sr cnt --	; fill CNT dword with V in DE
CMOVE   | de sr cnt --	; Copy CNT bytes from SR to DE
CMOVE>  | de sr cnt --	; Copy CNT bytes from SR to DE (reverse)
CFILL	| v sr cnt --	; fill CNT bytes with V in DE
```

## Memory and disk interection
```
MEM		| -- dir 				; Free memory start
LOAD	| d "filename" -- e		; Load to memory in D with "file", end in E
SAVE	| d n "filename" -- 	; Save from memory D, N bytes in "file"
APPEND	| d n "filename" -- 	; Append from memory D, N bytes in "file"

FFIRST  | "path" -- fdd/0		; Get First folder entry
FNEXT 	| -- fdd/0				; Get Next folder entry, 0 end of files.
```

## Conection with SO
```
UPDATE	| s -- s		; update the event loop of SO
MSEC 	| -- a 			; Get the miliseconds of SO
TIME 	| -- s m h 		; Get Hour Minutes and Seconds
DATE 	| -- d m a		; Get Day Mon and Age
END 	| --			; end program

RUN  	| "nom" --			; Load, compile and execute a source file
SYSTEM	| "cmd" -- status	; Call system exec "cmd" or 0 end or -1 check state
```

## Graphics FrameBuffer words
```
SW 		| -- w		; Screen Width
SH 		| -- h		; Screen Heigth
REDRAW  | --		; Redraw the screen, is Double Buffer Video
FRAMEV	| -- m		; Start Video Memory, SW*SH*4 is the size

INK		| a --		; Set ink color
INK@	| -- a		; Get ink color
ALPHA 	| a --		; Set Transparency

OP 		| x y --	; Origin Point for draw
LINE 	| x y --	; Draw Line (antialiased)
CURVE 	| x y x y --	; Draw Curve
CURVE3 	| x y x y x y -- ; Draw Curve

PLINE 	| x y --	; Mark line for polygon
PCURVE 	| x y x y --	; Mark curve for polygon
PCURVE3 | x y x y x y --	; Mark curve for polygon

POLI	| --		; Fill Polygon

FCOL	| c1 c2 --	; Define two colors for degrade
FCEN	| x y --	; Degrade center
FMAT	| a b --	; Degrade matrix

SFILL	| --		; Set Fill polygon to solid
LFILL	| --		; Set Fill polygon to lineal degrade
RFILL	| --		; Set Fill polygon to radial degrade (close to)
```

## Mouse and Keyboad
```
XYMOUSE | -- x y 	; x y of pointer
BMOUSE	| -- b		; buttons of pointer
KEY		| -- s		; get Key (scancode)
KEY!	| v --    	; save to key (for modify)
```

## Joystick
```
CNTJOY	| -- cnt	; Number of Joysticks
GETJOY	| j -- a	; Info of Joy J
```

## Sound
```
SLOAD	| "" -- pp	; Load Sound (FMOD libary)
SPLAY	| pp -- 	; Play Sound (FMOD libary)
MLOAD	| "" -- mm	; Load Music (FMOD libary)
MPLAY	| mm --		; Play Music (FMOD libary)
```

## Web
```
OPENURL	| url header buff -- buff/0		; Open URL trow SO
```

## Printer
```
DOCINI	| --                    prepara pagina para imprimir
DOCEND	| --                    imprime pagina
DOCMOVE	| x y --				ubica cursor
DOCLINE	| x y --				dibuja linea
DOCTEXT	| "tt" --				imprime texto
DOCSIZE	| "tt" -- w h			obtiene tamaÃ±o de texto
DOCFONT	| size angle "font" --  elije fuente de letra
DOCBIT	| "file.bmp" x y --		imprime un bitmap (.bmp)
DOCRES	| -- xmax ymax     		retorna resolucion de impresora
```
