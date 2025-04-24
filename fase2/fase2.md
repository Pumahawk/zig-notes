---
id: LEARN-FASE-2-DETAILS
title: "Imparare zig 2 - Fondamentali del Linguaggio - Details"
tags: [ "status:todo", "next" ]
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
