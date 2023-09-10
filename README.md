# 🎁 Gift List Project

Welcome to the Gift List project! This application has been designed to distribute gifts, but there's a catch. Only those names on the list will receive them. The unique challenge is that the server can only store a 32-byte value in its memory. This value must be sufficient for the server to determine who is on the list.

## 🚀 Getting Started

Start by cloning the starter repository: [GiftList Repository](https://github.com/alirazacodes/merkle-giftlist.git). 

After cloning, navigate to the project's root directory and run the following command to install the necessary dependencies:

```bash
npm install
```

## 📂 Project Structure

The repository is divided into three primary folders:

### 1. Client

To run the client, execute the following command from the root directory:

```bash
node client/index
```

The client script sends an HTTP request to the server. In this context, consider the client as the **prover**. Its main responsibility is to prove to the server that a given `name` is indeed a part of the `MERKLE_ROOT`.

### 2. Server

To initialize the server, run:

```bash
node server/index
```

This command will launch an Express server on port 1225, waiting to respond to the client's requests. Here, the server acts as the **verifier**. Its task is to confirm that the `name` provided by the client exists within the `MERKLE_ROOT`. If the verification is successful, the gift will be dispatched!

### 3. Utils

The utils directory houses several crucial files:

- **niceList.json**: This file holds the names of the lucky recipients set to receive gifts this year. The list is randomly generated, but feel free to include your name or the names of your acquaintances!
  
- **example.js**: This script provides a demonstration of how to generate a root, create a proof, and verify the proof. To run this example, use:

  ```bash
  node utils/example.js
  ```

- **MerkleTree.js**: If you've worked with the Merkle Tree module before, this will be familiar. This version has been adjusted to eliminate any complications related to crypto type conversions. You can easily import it into your client/server.
  
- **verifyProof.js**: This is a carry-over from the final stage of the previous module. It can be utilized to confirm that a name belongs to the merkle root, as illustrated in the example.

## ✅ To-Do List

- [X] Prove to the server we're on the nice list.
- [X] Incorporate request body parameters.
- [X] Extract parameters from the front-end.
- [X] Embed a hardcoded merkle root representing the entire nice list.
- [X] Validate that a name is part of the list.

## 💡 Hints

Always view the client as the prover. They're the ones attempting to convince the server that a particular name is part of the list. On the other hand, the server acts as the verifier, using minimal information to authenticate that the name forwarded by the client is indeed on the list.

For everything related to the Merkle Tree, the `/utils` folder is your best friend. The `example.js` file provides a detailed walkthrough on generating a root, crafting a proof, and affirming that proof.

Remember, our MerkleTree implementation has been modified for your convenience! We've incorporated a few helpers from the `ethereum-cryptography` library to facilitate type conversions.
