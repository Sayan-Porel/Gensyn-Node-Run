# Aztec Node Timeout Fix Guide

## Fix TypeError: fetch failed → ConnectTimeoutError

This error occurs when the Aztec node can’t reach external resources (likely the L1 RPC or bootnode URLs).

---

## 1. Stop Your Node

```bash
CTRL + C
```

---

## 2. Enable Firewall

```bash
sudo ufw enable
```

---

## 3. Set Default Firewall Rules

```bash
sudo ufw default allow outgoing
sudo ufw default allow incoming
```

---

## 4. Allow Required Ports

```bash
sudo ufw allow 22/tcp
sudo ufw allow 8080/tcp
sudo ufw allow 40400/tcp
sudo ufw allow 40400/udp
sudo ufw allow 40500/tcp
```

---

## 5. Reload Firewall

```bash
sudo ufw reload
```

---

## 6. Check Firewall Status

```bash
sudo ufw status verbose
```

---

## 7. Update Aztec Node

```bash
aztec-up 0.85.0-alpha-testnet.98
```

---

## 8. Start Aztec Node

Replace the placeholders with actual values:

- `RPC_URL`
- `BEACON_URL`
- `0xYourPrivateKey`
- `0xYourAddress`
- `IP`

```bash
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL \
  --l1-consensus-host-urls BEACON_URL \
  --sequencer.validatorPrivateKey 0xYourPrivateKey \
  --sequencer.coinbase 0xYourAddress \
  --p2p.p2pIp IP \
  --p2p.maxTxPoolSize 1000000000
```
