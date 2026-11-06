# NIP-77 (Negentropy Sync) on LiberNet

> Negentropy Syncing, as used by the **LiberNet** apps.

**Official spec:** [nostr-protocol/nips · 77.md](https://github.com/nostr-protocol/nips/blob/master/77.md)
**Status upstream:** `draft` `optional` `relay`
**Maintainer of this repo:** Luciano "Barak" Casalunga ([@lucianocasalunga](https://github.com/lucianocasalunga)) · [libernet.app](https://libernet.app)

## My role

I took part in the creation of NIP-77, and it runs across the LiberNet apps.

## Why NIP-77 matters for LiberNet

LiberNet keeps several relays and apps in sync. NIP-77 (Negentropy) compares two event sets and transfers only what is missing, saving bandwidth for both relay-to-relay and app-to-relay sync. LiberNet announces `77` in its NIP-11 `supported_nips`.

## How it works (quick reference)

| Message | Direction | Purpose |
|---------|-----------|---------|
| `NEG-OPEN` | client → relay | Filter + initial Negentropy message (hex) |
| `NEG-MSG` | both | Reconciliation rounds |
| `NEG-ERR` | relay → client | Error (`blocked:`, `closed:`) |
| `NEG-CLOSE` | client → relay | End the sync |

After learning which IDs are missing, each side uses normal `EVENT` / `REQ` to move the events.

### Example

```
["NEG-OPEN", "sync1", {"kinds": [1], "since": 1730000000}, "<hex message>"]
["NEG-MSG", "sync1", "<hex message>"]
["NEG-CLOSE", "sync1"]
```

## Related LiberNet NIPs

[NIP-43](https://github.com/lucianocasalunga/nip-43) · [NIP-45](https://github.com/lucianocasalunga/nip-45) · [NIP-50](https://github.com/lucianocasalunga/nip-50) · [NIP-66](https://github.com/lucianocasalunga/nip-66) · [NIP-67](https://github.com/lucianocasalunga/nip-67) · [NIP-70](https://github.com/lucianocasalunga/nip-70) · [NIP-86](https://github.com/lucianocasalunga/nip-86) · [NIP-95 (my proposal)](https://github.com/lucianocasalunga/nip-95)

---
Nostr since 2021 · Part of the LiberNet ecosystem
