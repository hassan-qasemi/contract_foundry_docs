# 📘 How-To Guides

This section provides step-by-step instructions for using Contract Foundry’s features via the official Android wallet application. All operations—from identity creation to smart contract deployment—are executed locally on your device, ensuring secure, self-sovereign interaction with the blockchain.

> ⚠️ **Note**: All actions require a EOA as delegate and for deployment an active subscription plan or account charge based on usage needs.

---

## 🔐 1. Setting Up Your Wallet & Private Key

Before using any service, funded EOA required.

### Steps:

1. **Open the Contract Foundry wallet app**.
2. Tap **“Wallet”** and choose:
   * **Generate New Key** or
   * **Import Existing Private Key**.
3. Your key will be securely stored in **encrypted local storage**.
4. Embalance EOA to cover network gas fees.
5. (Optional) Set up passcode protection for local access.

---

## 🆔 2. Creating and Managing a Decentralized Identity (DID)

Use this process to register a new blockchain-based identity compliant with ERC-1056 and W3C standards.

### Steps:

<img src=images/nav_did.png alt="Alt text" width="200"/>

1. Navigate to **“DID”**, Tap **“Create DID”** and choose DID type to create *(example is for Ether DID)*.

<img src=images/did_info.png alt="Alt text" width="200"/>

2. Fill in the **DID name**, **network**, and public informations.
3. Tap **“Continue”** and sign the transaction with your private key.

<img src=images/init_did.png alt="Alt text" width="200"/>
<img src=images/did_init_history.png alt="Alt text" width="200"/>

4. Once deployed, in history page and issuance tile tap **“Initialize & setup”** to activate it.

<img src=images/did_page.png alt="Alt text" width="200"/>
<img src=images/diddoc_load.png alt="Alt text" width="200"/>
<img src=images/diddoc.png alt="Alt text" width="200"/>

5. Manage controllers, delegates, and services from the DID dashboard.

---

## 🧾 3. Deploying a Smart Contract

You can deploy multiple types of contracts.

### Steps:

1. Go to **“Contracts”** > Select a contract type:

   * Verifiable Document
   * Pledge
   * Asset Paywall
2. Fill out the form with necessary details (title, reference, pricing, etc.).
3. Tap **“Deploy Contract”** and confirm the transaction.
4. Once confirmed, go to **“History”** and tap **“Initialize”** to activate the contract.
5. Share the **Contract DID** with relevant parties to interact.

---

## 📜 4. Issuing a Verifiable Credential

Create tamper-proof credentials for yourself or others using a visual editor.

### Steps:

<img src=images/vc_page.png alt="Alt text" width="200"/>

1. Go to **“Credentials”** > Tap **“New Verifiable Entity”**.

<img src=images/vc_page_dialog.png alt="Alt text" width="200"/>

2. Select **“Credential”** as the entity type.

<img src=images/vc_form.png alt="Alt text" width="200"/>

3. Enter the **issuer DID** (your identity or a key-based DID).

<img src=images/vc_subject_field_dialog.png alt="Alt text" width="200"/>
<img src=images/vc_subject_page.png alt="Alt text" width="200"/>

4. Define the **credential subject**, **schema**, and optional metadata.
5. Tap **“Generate Credential”** and sign with your private key.

> ✅ The credential will appear in your wallet and can be exported.

---

## ✅ 5. Verifying or Updating a Credential

Verify the authenticity of a credential or update its status.

### To Verify a Credential:

<img src=images/vc_page2.png alt="Alt text" width="200"/>

1. Open the credential from your **VC list**.

<img src=images/vc_page_dialog.png alt="Alt text" width="200"/>
<img src=images/vc_display.png alt="Alt text" width="200"/>

2. Tap **“Verify”** from the top-right menu.
3. Input the **signer DID** and your **private key** to confirm.

<img src=images/verified_vc_display.png alt="Alt text" width="200"/>

4. Verification proof will be appended to the VC.

### To Update Credential Status:

1. Tap **“More”** > **“Update Status”**.
2. Select one of the following: **Valid**, **Suspended**, **Revoked**.
3. Sign/verify the credentials with your private key.

> 📝 Only the issuer DID can perform status updates.

---

## 💰 6. Using the Pledge Contract

Perfect for freelancers, service providers, and milestone-based payment agreements.

### For Service Providers:

1. Go to **“Contracts”** > **“Pledge Contract”**.

<img src=images/pledge_form.png alt="Alt text" width="200"/>

2. Fill in service details, total cost in chosen network currency in (WEI) unit.

<img src=images/init_pledge.png alt="Alt text" width="200"/>

3. Deploy and initialize the contract.

<img src=images/pledge_info.png alt="Alt text" width="200"/>
<img src=images/load_pledge.png alt="Alt text" width="200"/>
<br/>
<img src=images/pledge_page.png alt="Alt text" width="200"/>
<img src=images/pledge_options.png alt="Alt text" width="200"/>

4. Share the **Contract DID** with the customer.

### For Customers:

1. Open the contract using the shared DID.
2. Submit payments per milestone or full upfront.
3. Confirm **“Service Complete”** when work is finished.

> 🔐 Funds are locked until the customer approves service completion.

---

## 📂 7. Creating a Verifiable Presentation (VP)

Combine multiple VCs into a single presentation file.

### Steps:

1. Go to **“Credentials”** > Tap **“New Verifiable Entity”**.
2. Enter the **issuer DID** (your identity or a key-based DID).
3. Select VCs from your list.
4. Tap **“Create Presentation”** and sign.
5. The presentation is stored in your wallet and can be exported manually.

---

## 📦 8. Exporting and Sharing credentials

All credentials, presentations, and document references can be exported as JSON files.

### To Export:

1. Open the credentials page.
2. Tap **“Export”**, file will be created in **"Download"** folder in internal storage.

### Sharing Options:

* Share file manually via email or messaging apps.
* Upload to IPFS or Arweave for decentralized access (optional).

---

These guides are designed to help both new and experienced users confidently navigate and utilize the full suite of Contract Foundry services through the mobile app. For troubleshooting or in-app help, refer to the **Support** or **FAQ** section in the main menu.
