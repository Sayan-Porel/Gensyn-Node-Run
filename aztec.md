<div align="center">
  <div style="display: flex; align-items: center;">
    <img src="https://raw.githubusercontent.com/AirdropScriptFA/CryptoTechLooter/796c2e77cdef9dbd6d7ced6fc1aab995e640a153/IMG_20250518_151850_367.jpg" alt="CryptoTechLooter Logo" width="100" style="margin-right: 20px;"/>
    <div>
      <b>This Codes/Software Is Shared By <a href="https://t.me/cryptotechlooter">Crypto Tech Looter</a></b>
    </div>
  </div>
</div>

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
