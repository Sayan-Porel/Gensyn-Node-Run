
# Aztec Alpha Testnet Node Guide

This repository provides instructions to manage, update, and monitor your Aztec Alpha Testnet node.

---

## Prerequisites

- Docker installed
- Access to your Validator Private Key, Coinbase Address, and Public IP
- Valid RPC URLs for Ethereum Sepolia and Beacon nodes

---

## 1. Stop the Running Node

If your node is running, stop it using:

```bash
CTRL + C
```

---

## 2. Clean Old Data

Remove all previous node data:

```bash
rm -rf ~/.aztec/alpha-testnet/data/
```

---

## 3. Update the Node

Fetch the latest version of the Alpha Testnet:

```bash
aztec-up alpha-testnet
```

---

## 4. Rerun the Node with Updated RPC

**Replace the following placeholders:**
- `0xYourPrivateKey` with your validator's private key
- `YourAddress` with your sequencer coinbase address
- `Your_ip` with your public IP address
- `Eth_Sepolia_RPC` and `Eth-beacon_sepolia_RPC` with valid RPC endpoints

```bash
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls Eth_Sepolia_RPC \
  --l1-consensus-host-urls Eth-beacon_sepolia_RPC \
  --sequencer.validatorPrivateKey 0xYourPrivateKey \
  --sequencer.coinbase YourAddress \
  --p2p.p2pIp Your_ip
```

---

## 5. Check Node Logs

To verify that the node is working correctly:

```bash
sudo docker logs -f --tail 100 $(docker ps -q --filter ancestor=aztecprotocol/aztec:latest | head -n 1)
```

---

## 6. Stop the Node via Docker

If needed, stop the Docker container running the node:

```bash
sudo docker stop $(docker ps -q --filter ancestor=aztecprotocol/aztec:latest | head -n 1)
```

---

## 7. Reload Firewall Rules (Optional)

```bash
sudo ufw allow ssh
sudo ufw reload
```

---

> ##  Use Different AI Models to Scan File

> You should use different AI-based security scanners or antivirus engines to continuously scan files for malicious activity. Keeping scanning active helps ensure safety when dealing with unknown or external data.

---

## Source

Telegram : [Crypto Tech Looter](https://t.me/cryptotechlooter)

---
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
