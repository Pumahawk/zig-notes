---
id: LEARN-FASE-2-DETAILS
title: "Imparare zig 2 - Fondamentali del Linguaggio - Details"
tags: [ "status:todo" ]
---

# Imparare zig 2 - Fondamentali del Linguaggio

## Numeri

Zig offre una varietà di tipi numerici.

Possiamo dividerli in:

- Quelli che permettono di rappresentare numeri **positivi**.
- Quelli che permettono di rappresentare numeri **sia positivi che negativi**.
- Per la quantità di **memoria che occupanto**.


### Interi Signed

Possono rappresentare sia numeri positivi che negativi, la **i** sta per **integer**, seguiti dal **numero di bit**.

- **i8**: Intero signed a 8 bit (da -128 a 127).
- **i16**: Intero signed a 16 bit (da -32768 a 32767).
- **i32**: Intero signed a 32 bit (da -2147483648 a 2147483647).
- **i64**: Intero signed a 64 bit.
- **i128**: Intero signed a 128 bit.
- **isize**: Intero signed con la **stessa dimensione di un puntatore** (dipende dall'architettura del sistema, tipicamente 32 o 64 bit). Usato spesso per indicizzare array o rappresentare dimensioni di memoria.

### Interi Unsigned

Questi tipo possono rappresentare soltanto numeri positivi, la **u** sta per **unsigned**, seguito dal **numero di bit**.

- **u8**: Intero unsigned a 8 bit (da 0 a 255).
- **u16**: Intero unsigned a 16 bit (da 0 a 65535).
- **u32**: Intero unsigned a 32 bit (da 0 a 4294967295).
- **u64**: Intero unsigned a 64 bit.
- **u128**: Intero unsigned a 128 bit.
- **usize**: Intero unsigned con la **stessa dimensione di un puntatore**. Usato spesso per rappresentare dimensioni e indici.

### Floating point

Questi tipi possono rappresenare numeri con la la parte frazionaria.

- **f32**: Floating-point a 32 bit (precisione singola).
- **f64**: Floating-point a 64 bit (doppia precisione).

## Booleani

Possono rappresentare soltanto 2 valori. `true`, `false`.

## Caratteri

I caratteri sono di tipo **u8** questo perché zig adotta la codifica **UTF-8**. I caratteri **Unicode** possono essere rappresentati da uno o più byte.

```zig
const c1: u8 = 'A'; // num value: 65
const c2: u8 = '€'; // Invalid operation
```

**Output**:

```
code/fase2-chars.zig:6:20: error: type 'u8' cannot represent integer value '8364'
    const c2: u8 = '€';
```

Per lavorare con stringhe di testo più completo si utilizzano slices di byte (`[]const u8`)

## `void`

Utilizzato per rappresentare l'assenza di valore. Utilizzato per rappresentare il ritorno di una funzione che non restituisce un valore segnificativo.

## `null` e tipi opzionali `?T`

Zig gestisce in modo sicuro il valore null tramite l'optional.

- `null` può essere assegnato ad un tipo di puntatore o ad un valore opzionale.
- Tipi opzionali (`?T`): Aggiungendo `?` davanti ad un tipo che non sia un puntatore o un valore opzionale, si crea un valore nuovo che può essere di tipo
        T oppure opzionale.

è possibile fare l'unwrap del valore nullo all'interno dell'if

```
if (var_name) |non_null_var_name| ... else ...
```

## Array e Slices

- Array (`[n]T`): è una sequenza di dimensione **fissa** di elementi dello **stesso tipo** dove **n** è una dimensione **costante in fase di compilazione**.
- Slice (`[]T`): è una **vista dinameica** su una sequenza di elementi (che potrebbe essere un array o un altro slice.

Uno slice **non** possiede i dati sottostanti ma **contiene un puntatore ad un elemento e una lunghezza**.
Siccome la dimenzione non fa parte del tipo, gli slice sono più flessibili.

## Stringhe

Le stringhe normalmente sono rappresentate come slice di byte. (`const[] u8`) che contengono dati codificati in UTF-8. La parte const indica che contiene
dati immutabili.

Importante comprendere che zig non ha una rappresentazione dedicata delle stringhe come in altri linguaggi. Per operazioni più elaborate potrebbe essere necessario
gestire direttamente la memoria.


## Variabili e costanti

In zig per dichiarare le variabili e costanti si utilizzando le parole chiave `var` e `const`.

- `var` sono contenitori il cui valore può cambiare (mutato) durante l'esecuzione del programma.
- `const` sono contenitori il cui valore non può cambiare.

## Inferenza di tipo

Il programma può in automatico capire il valore delle variabili durante la loro creazione. Per questo non è
necessario specificare sempre il tipo. Lo si può per rendeere il programma più esplicito.

```
var num1: u32 = 1_000;
const num2: u32 = 1_000;

const num3 = 100; // Inferenza di tipo.
```

## Mutabilità e immutabilità

La mutabilità e la immutabilità dei dati si gestisce definiendo le variabili con `const` o `var`.
E' una buona convenzione cercare di utilizzare const quando si dichiara una variabile cosi da avere
la certezza che questa variabile non venva modificata nel tempo per errore.

Dichiarare una variabile come `var` esplicitamente soltanto se una variabile deve cambiare nel tempo.

Avere una variabile non mutabile dichiarata esplicitamente permete di evitare modifiche involotarie ai dati.


 ## Operatori

 Un classico della programmazione. Nulla di speciale. A seguire una carrellata degli operatori più usati.

- Aritmetici: +, -, *, /, %
- Confronto: ==, !=, <, >, <=, >=
- Operatori logici: and, or, !
- Operatori di Assegnamento (=, +=, -=, *=, /=, %=, &=, |=, ^=, <<=, >>=)

Operatori meno utilizzati (da me) sono gli operatori di **Bitwise**.

- `&` (AND bit a bit): Esegue un AND bit per bit tra i due operandi.
- `|` (OR bit a bit): Esegue un OR bit per bit tra i due operandi.
- `^` (XOR bit a bit): Esegue un XOR (OR esclusivo) bit per bit tra i due operandi.
- `~` (NOT bit a bit): Inverte i bit dell'operando (unario).
- `<<` (Scorrimento a sinistra): Sposta i bit del primo operando a sinistra per il numero di posizioni specificato dal secondo operando.
- `>>` (Scorrimento a destra): Sposta i bit del primo operando a destra per il numero di posizioni specificato dal secondo operando.

A cosa servono gli operatori **Bitwise**?

- Manipolazione di Flag (Set di Bit)
- Operazioni a Basso Livello e con Hardware
- Grafica e Manipolazione di Immagini
- Compressione e Decompressione Dati
- Crittografia

## Strutture di controllo del Flusso

### **if**, **else**, **else if**

```
if (condizione) { ... }
if (condizione) { ... } else { ... }
if (condizione) { ... } else if (condizione) { ... }
```

In oltre permette di fare un unwrapping del valore optional.

```
if (var_optional) |var_se_presente| { ... }
```

L' `if` può essere utilizzato anche durante l'assegnazione.

### **while** e **for** loop (con iteratori)

TODO...

### **switch** statement

TODO...

### **break** e **continue**

TODO...

