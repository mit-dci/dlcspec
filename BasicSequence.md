# Sequence

This document is the basic sequence.

## Assumptions

- Alice and Bob are already matched.
- Alice and Bob have a means of communication.

# Contract

    +-------+                      +-------+
    |       |                      |       |
    |       |--(1)--- offer  ----->|       |
    |       |                      |       |
    |       |<-(2)--- accept ------|       |
    | Alice |                      |  Bob  |
    |       |--(3)--- sign   ----->|       |
    |       |                      |       |
    |       |                      |  (4) send fund-tx
    |       |                      |       |
    +-------+                      +-------+


---
## (1) Offer

Alice send data to Bob.

### 1. Contract information

This parameter is information that allows Alict and Bob to decide how to become from the Fund by Oracle message.

Example.
- product
- product amount
- time
- etc...

### 2. Oracle information

This parameter is information that Oracle can identify.

### 3. Alice fund amount (satoshi)

This parameter is Alice's fund amount (including payment transaction fee).

### 4. Alice public key

This public key is used for fund-tx(2-of-2 multisig).

### 5. Alice inputs

Alice's input used for fund-tx.

### 6. Alice output(option)

If Alice's change is necessary, it is the address.

### 7. Estimatesmartfee (satoshi/kbyte)

This parameter is used for fund transactions and settlement transactions.

### 8. Delay (option)

It does not make much sense in DLC, 144 fixed may be good.

### 9. Refund locktime

This is refund transaction locktime.

---
## (2) Accept

If Bob is good at that condition, Bob send data to Alice.

### 1. Bob fund amount (satoshi)

This parameter is Bob's fund amount (including payment transaction fee).

### 2. Bob public key

This public key is used for fund-tx(2-of-2 multisig).

### 3. Bob inputs

Bob's input used for fund-tx.

### 4. Bob output(option)

If Bob's change is necessary, it is the address.

### 5. Settlement signs

This is all settlement transaction Bob's signatures.

### 6. Refund Sign

This is refund transaction Bob's signature.

---
## (2)' Refuse

If Bob is not good at that condition, Bob send data to Alice.

### 1. Message

---

## (3) Sign

Alice validates the (2) data.

If check is ok, Alice two data to Bob.

### 1. Fund transaction signs

This is fund transaction Alice's signatures.

### 2. Settlement signs

This is all settlement transaction Alice's signatures.

### 3. Refund sign

This is refund transaction Alice's signature.

---

## (4) Send fund-tx

Bob validates the (3) data.

If check is ok, Bob signs fund-tx.

Bob sends fund-tx to Bitcoin.

When fund-tx enters the block, the contract is completion.

---