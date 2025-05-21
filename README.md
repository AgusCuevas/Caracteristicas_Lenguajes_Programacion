# Caracteristicas_Lenguajes_Programacion
# TP 1

```mermaid
flowchart TD

subgraph DEF["Definición"]
    direction LR
    C["Especificación de tareas computacionales"]
    D["Notación para escribir programas"]
    E["Herramientas fundamentales para la comunicación entre humanos y computadoras"]
end

subgraph HLP["Historia de los LP"]
    direction TB
    H1["Antes de 1940: Programación mediante cableado"] --> H3["Década de 1940: Uso de códigos (Von Neumann). Evita el cableado"]
    H3 --> H4["Lenguaje ensamblador: Lenguaje de bajo nivel que facilitaba la programación mediante abreviaturas"]
    H4 --> H5["Adición de construcciones de alto nivel"]
    H5 --> H6["Transición a lenguajes de alto nivel"]
    H6 --> H7["Independencia de la máquina: Los LP modernos se independizaron de la máquina"]
end

subgraph DDP["Definición de paradigmas"]
    direction TB
    DP1["Conjunto de conceptos"] --> DP2["Cada paradigma tiene su propio enfoque"] --> DP3["Muchos lenguajes soportan más de un paradigma"]
end

subgraph PDP["Paradigmas de Programación"]
    direction TB
    P1["Paradigma Imperativo"] --> PI1["Secuencia de instrucciones"]
    PI1 --> PI2["Uso de variables, selección e iteración"] --> PI3["Ejemplos: C, Fortran, Pascal"]

    P2["Paradigma Orientado a Objetos"] --> POO1["Clases y objetos"]
    POO1 --> POO2["Encapsulamiento, polimorfismo, herencia"] --> POO3["Ejemplos: Java, Python, C++"]

    P3["Paradigma Funcional"] --> PF1["Cálculo lambda y funciones como parámetros"]
    PF1 --> PF2["Evaluación diferida y transparencia referencial"] --> PF3["Ejemplos: Haskell, Scala, F#"]

    P4["Paradigma Lógico"] --> PL1["Hechos y reglas (Cláusulas de Horn)"]
    PL1 --> PL2["Deducción mediante unificación y backtracking"] --> PL3["Ejemplos: Prolog, Mercury"]
end

LP["Lenguajes de Programación (LP)"] --> DEF
LP --> HLP
LP --> DDP
DDP --> PDP
```
# TP 3

# Gramáticas Formales para Emojicode: GIC, BNF, EBNF y ABNF

Emojicode es un lenguaje de programación esotérico de propósito general que utiliza emojis como elementos sintácticos primarios. Representa una fusión única entre:

Semántica de lenguajes convencionales (como Python o Java)

Sintaxis basada completamente en Unicode Emoji

Paradigmas de programación orientada a objetos y procedural

### Origen y Filosofía:
Creado en 2016 por Theo Weidmann, surge como crítica/exploración de:

La universalidad de los emojis como lenguaje visual global

La posibilidad de construir sistemas formales sobre símbolos no tradicionales

Un experimento sobre cognición y programación

## 1. GIC (Gramática Independiente del Contexto) para Emojicode

```plaintext
Programa       → 🏁 Bloque 🍉
Bloque         → Instrucción Bloque | Instrucción | λ
Instrucción    → Imprimir | Declaración | Bucle | Condicional | λ
Imprimir       → 😀 Expresión
Declaración    → 🍿 Variable Expresión
Bucle          → 🔁 Expresión ( Bloque )
Condicional    → 🤔 Operación ( Bloque ) | 🤔 Operación ( Bloque ) 🙁 ( Bloque ) 
Expresión      → 🔤Texto🔤 | Variable | Número | Operación
Operación      → Expresión Operador Expresión
Operador       → ➕ | ➖ | ✖️ | ➗ | ✍️
Variable       → A|B|C| ... |Z|a|b|c|...|z
Número         → 0|1|...|9
Texto          → Variable | Número     
```

---

## 2. BNF para Emojicode


```bnf
<Programa>    ::= 🏁 <Bloque> 🍉
<Bloque>      ::= <Instrucción> <Bloque> | λ
<Instrucción> ::= <Imprimir> | <Declaracion> | <Bucle> | <Condicional>
<Imprimir>    ::= 😀 <Expresión>
<Declaracion> ::= 🍿 <Variable> <Expresión>
<Bucle>       ::= 🔁 <Expresión> <Bloque>
<Condicional> ::= 🤔 <Operación> <Bloque> [🙁 <Bloque>]
<Expresión>   ::= 🔤<Texto>🔤 | <Variable> | <Número> | <Operación>
<Operación>   ::= <Expresión> <Operador> <Expresión>
<Operador>    ::= ➕ | ➖ | ✖️ | ➗ | ✍️
<Variable>    ::= A|B|C| ... |Z|a|b|c|...|z
<Número>      ::= 0|1|...|9
<Texto>       ::= <Variable> | <Número> 
```
---

## 3. EBNF para Emojicode

```ebnf
Programa     = 🏁 Bloque 🍉

Bloque       = { Instrucción }

Instrucción  = Imprimir | Declaración | Bucle | Condicional

Imprimir     = 😀 Expresión;

Declaración  = 🍿 Variable Expresión  

Bucle        = 🔁 Expresión Bloque

Condicional  = 🤔 Operación Bloque [🙁 Bloque]

Expresión    = 🔤Texto🔤 | Variable | Número | Operación | "(" Expresión ")"

Operación    = Expresión Operador Expresión

Operador     = ➕ | ➖ | ✖️  | ➗ | ✍️

Variable     = letra { letra | digito | _ }*

Número       = [ + | - ] digito { digito }*

Texto        = { letra* | digito* } 

letra       =  A | ... | Z | a | ... | z

digito        = 0 | ... | 9
```

---

## 4. ABNF para Emojicode


```abnf
programa : 🏁  
           bloque 
           🍉  

bloque : instruccion 
         bloque instruccion

instruccion : 😀 expresion  
              🍿 variable expresion  
              🔁 expresion bloque  
              🤔 Operación bloque 🙁 bloque

expresion : 🔤 cadena 🔤 
            numero
            variable
            operacion
            ( expresion )

numero : signo _op 
         digito _op

signo : uno de + -

digito : uno de 0-9

operacion : expresion 
            operador 
            expresion

operador : uno de ➕ ➖ ✖️ ➗ ✍️

variable : letra _op 
           letraodigito _op

letraodigito : uno de letra digito

letra : una de a-z A-Z

cadena : uno de numero letra
```
---

## Ejemplo Práctico Comparado

**Programa en Emojicode:**

```emojicode
🏁
  😀 🔤Hola🔤
  🍿 x 10
  🤔 x ➖ 1 ✖️ 2 🙁
    😀 🔤x es par🔤
  🙁
    😀 🔤x es impar🔤
  🔁 x 😀 x 🍿 x x ➖ 1
🍉
```
**Programa en Python:**

```Python
print("Hola")
x = 10
while x > 0:
    if x % 2 == 0:
        print(f"{x} es par")
    else:
        print(f"{x} es impar")
    x -= 1
```

---
# TP 4
## Arbol de Análisis Sintáctico de un Programa Fuente
```
🏁
  🍿 i 0
  🔁 i <= 5 (
    🤔 i ➗ 2 == ✍️ 0(
      😀 🔤Par🔤 i
    ) 🙁 (
      😀 🔤Impar🔤 i
    )
    🍿 i i + 1
  )
🍉
```

``` mermaid
graph TD
    START[🏁] --> B1[Bloque]
    
    B1 --> I1[Instrucción]
    I1 --> D1[Declaración]
    D1 --> POP[🍿]
    D1 --> VAR[Variable]
    VAR --> i[i]
    D1 --> EXPR1[Expresión]
    EXPR1 --> NUM[Numero]
    NUM --> cero[0]
    
    I1 --> B2[Bloque]
    B2 --> I2[Instrucción]
    I2 --> C1[Condicional]
    C1 --> emoji1[🤔]
    
    C1 --> OP1[Operación]
    OP1 --> EXPR2[Expresión]
    EXPR2 --> VAR2[Variable]
    VAR2 --> i2[i]
    OP1 --> OPER[Operador]
    OPER --> div[➗]
    OP1 --> EX2[Expresión]
    EX2 --> OP2[Operación]
    OP2 --> EXPR6[Expresión]
    EXPR6 --> DOS[2]
    OP2 --> OPER2[Operador]
    OPER2 --> igu["✍️"]
    OP2 --> EXPR7[Expresión]
    EXPR7 --> CERO[0]
    C1 --> parIzq1["("]
    
    C1 --> B3[Bloque]
    B3 --> I3[Instrucción]
    I3 --> IMP1[Imprimir]
    IMP1 --> emoji2[😀]
    IMP1 --> EXPR4[Expresión]
    EXPR4 --> comilla1[🔤]
    EXPR4 --> TXT1[Texto]
    TXT1 --> par["Par"]
    EXPR4 --> comilla2[🔤]
    
    C1 --> parDer1[")"]
    
    I2 --> B4[Bloque]
    B4 --> I4[Instrucción]
    I4 --> C2[Condicional]
    C2 --> emoji3[🙁]
    
    C2 --> parIzq2["("]
    
    C2 --> B5[Bloque]
    B5 --> I5[Instrucción]
    I5 --> IMP2[Imprimir]
    IMP2 --> EXPR5[Expresión]
    EXPR5 --> comilla3[🔤]
    EXPR5 --> TXT2[Texto]
    TXT2 --> impar["Impar"]
    EXPR5 --> comilla4[🔤]
    
    C2 --> parDer2[")"]
    
    START --> END[🍉]
```

## Diagrama sintáctico de EMOJICODE
![image](https://github.com/AgusCuevas/Caracteristicas_Lenguajes_Programacion/blob/main/Diagramas%20sint%C3%A1cticos%20P1.jpeg)

![image](https://github.com/AgusCuevas/Caracteristicas_Lenguajes_Programacion/blob/main/Diagramas%20sint%C3%A1cticos%20P2.jpeg)

![image](https://github.com/AgusCuevas/Caracteristicas_Lenguajes_Programacion/blob/main/Diagramas%20sint%C3%A1cticos%20P3.jpeg)
