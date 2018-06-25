# Transaction and Script

## Fund

### Transaction

Transaction `version` is `2(0x02000000)`.

Inputs sequence is `0xffffffff(4294967295)`.

    Inputs:
        <alice input 1>
        <alice input : (option)>
        <alice input n (option)>
        <Bob   input 1>
        <Bob   input : (option)>
        <Bob   input m (option)>
    Outputs:
        <fund script (p2wsh)>
        <alice change public key (option)>
        <bob   change public key (option)>

LockTime is `0x00000000(0)`.

### Script

Fund script (p2wsh).

    OP_2
        <alice public key>
        <bob   public key>
    OP_2
    OP_CHECKMULTISIG

---

## Settlement


### Transaction

Transaction `version` is `2(0x02000000)`.

Inputs sequence is `0xffffffff(4294967295)`.

    Inputs:
        <fund input (fund transaction:0)>
    Outputs:
        <settletment script  (p2wsh)>
        <bob/alice public key>

LockTime is `0x00000000(0)`.

### Script

Settletment script  (p2wsh).

    OP_1
    OP_EQUAL
    OP_IF
        <alice/bob public key> + <oracle message key>
    OP_ELSE
        <delay>
        OP_CHECKSEQUENCEVERIFY
        OP_DROP
        <bob/alice public key>
    OP_ENDIF
    OP_CHECKSIG

---

## Refund

### Transaction

Transaction `version` is `2(0x02000000)`.

__Inputs sequence is `0xfeffffff(4294967294)`.__

    Inputs:
        <fund input (fund transaction:0)>
    Outputs:
        <alice public key>
        <bob   public key>

__LockTime is late time than oracle announces.__

---

