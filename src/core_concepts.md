# 📘 Core Concepts

Understanding the foundational principles behind Contract Foundry is key to leveraging its full capabilities. This section explains the essential components that make up the platform’s decentralized infrastructure, from identity and credentials to smart contracts and cryptographic signatures.

---

## 1. Decentralized Identity (DID)

A **Decentralized Identity (DID)** is a blockchain-based identity that belongs entirely to its creator. Unlike traditional identity systems that depend on centralized databases or issuing authorities, DIDs allow users to own and manage their digital presence independently.

Contract Foundry implements DIDs using the **ERC-1056** standard, ensuring compatibility with Ethereum and alignment with **W3C DID** specifications.

### Key Components of a DID:

* **Controller**: The primary account or key that controls the identity. This can update delegates and manage services.
* **Delegates**: Secondary keys with specific roles like signing, encryption or acting on behalf of the controller.
* **Services**: URL-based entries used to associate the DID with other metadata, APIs, or public keys.

### Use Cases:

* Personal or organizational identity
* Verification for credential issuance
* Authenticated smart contract interactions

---

## 2. Verifiable Credentials (VC)

**Verifiable Credentials** are digitally signed statements that assert facts about an identity. These can represent qualifications, licenses, achievements, or any attribute tied to an individual or organization.

Contract Foundry supports the **W3C VC data model**, allowing for cross-platform compatibility and decentralized verification.

### Structure of a VC:

* **Issuer DID**: The identity that signs and issues the credential.
* **Subject**: The entity the credential refers to.
* **Credential Metadata**: Includes information like credential type, expiration, issuance date.
* **Proof**: A cryptographic signature linking the issuer DID with the credential content.

### Capabilities:

* Issue credentials using forms and document references
* Store credentials locally or export them
* Support credential verification, revocation, and suspension

---

## 3. Smart Legal Contracts

**Smart Contracts** are self-executing digital agreements that live on the blockchain. Contract Foundry offers a suite of **pre-built legal-grade smart contracts**, requiring no coding to deploy.

### Core Contracts:

* **Verifiable Document Contract**: Ties a file to a legal identity with expiration and revocation options.
* **Pledge Contract**: Milestone-based escrow for service-based payments.
* **Asset Paywall**: Enables digital asset sales with pay-to-access logic.

### Features:

* Conditions encoded in contract logic
* Full automation without intermediaries
* Immutable, tamper-proof execution

---

## 4. Blockchain-Powered Digital Signatures

Digital signatures in Contract Foundry are used to validate documents, credentials, and contract interactions. These signatures are cryptographically secure and legally recognized under frameworks like **eIDAS** (EU) and **ESIGN** (US).

### Types of Signatures:

* **Identified Signatures**: Tied to a user’s DID, providing full auditability and legal weight.
* **Anonymous Signatures**: Detached from a formal identity, useful for privacy-preserving applications.

### How It Works:

* All signing operations occur locally within the Contract Foundry wallet app.
* Private keys are never transmitted and are stored in encrypted local storage.
* Signed data includes a timestamp and origin proof, creating a verifiable audit trail.

---

## 5. Storage & Integrity Mechanism

To maintain the integrity of off-chain data (like documents or credentials), Contract Foundry uses reference hashes stored on-chain.

### Supported Storage Types:

* **IPFS (InterPlanetary File System)**: Content-addressable, decentralized file system.
* **Arweave**: Permanent, blockchain-based storage with transaction ID references.
* **User-Hosted URIs**: Centralized storage maintained by the user, with integrity protected via immutable references.

This hybrid approach ensures flexibility in storage while guaranteeing authenticity and tamper detection.

---

## 6. Self-Sovereignty and Data Ownership

A central philosophy behind Contract Foundry is **self-sovereignty**, users fully own their data, identities and assets.

* **No Custody of Keys**: The platform never stores user private keys.
* **Encrypted Local Storage**: All data resides securely on the user’s mobile device.

This model puts control and trust exactly where it belongs: in the hands of the user.
