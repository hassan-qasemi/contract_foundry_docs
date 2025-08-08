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
1. Navigate to **“DID”**, Tap **“Create DID”** and choose DID type to create *(example is for Ether DID)*.
2. Fill in the **DID name**, **network**, and public informations.
3. Tap **“Continue”** and confirm the transaction with your private key as identity.
4. Manage controllers, delegates, and services from the DID dashboard.

---

## 📜 3. Issuing a Verifiable Credential

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

## ✅ 4. Verifying or Updating a Credential

Verify the authenticity of a credential or update its status.

### To Verify a Credential:

<img src=images/vc_page2.png alt="Alt text" width="200"/>

1. Open the credential from your **Credentials list**.

<img src=images/vc_page_dialog.png alt="Alt text" width="200"/>
<img src=images/vc_display.png alt="Alt text" width="200"/>

2. Tap **“Verify”** from the top-right menu.
3. Input the **verififer DID** and your **private key** to confirm.

<img src=images/verified_vc_display.png alt="Alt text" width="200"/>

4. Verification proof will be appended to the VC.

### To Update Credential Status:

1. Tap **“More”** > **“Update Status”**.
2. Select one of the following: **Valid**, **Suspended**, **Revoked**.
3. Sign/verify the credentials with your private key.

> 📝 Only the issuer DID can perform status updates.

---

## 💰 5. Using the Pledge Contract

Perfect for freelancers, service providers, and milestone-based payment agreements.

### For Service Providers:

1. Go to **“Contracts”** > **“Pledge Contract”**.

2. Fill in service details, total cost in chosen network currency in (WEI) unit.

3. Deploy and initialize the contract.

4. Share the **Contract DID** with the customer.

### For Customers:

1. Open the contract using the shared DID.
2. Submit payments per milestone or full upfront.
3. Confirm **“Service Complete”** when work is finished.

### Contarct Status Guide:

#### 1. `pending`

* **Meaning**: Service is initialized but **not started** yet.
* **Entered by**: No one, its default state.
* **Who can act**: Only the **seller** (issuer).
* **Transitions to**:

  * `active` → when seller start service
  * `canceled` → when seller cancels before starting
* **Permissions**:

  * ✅ Rollback: ✅ Allowed (buyer)
  * ✅ Cancel: ✅ Allowed (seller)
  * 🚫 Withdraw: ❌ Not allowed

---

#### 2. `active`

* **Meaning**: Service has been started and is in progress.
* **Entered by**: Seller start the service
* **Who can act**: Seller (to execute); Buyer (to dispute, after execute).
* **Transitions to**:

  * `executed` → when seller exceute service (marks delivery)
  * `disputed` → if buyer raises dispute while service is still active (on going)
* **Permissions**:

  * 🚫 Rollback: ❌ Not allowed (buyer), unless expired
  * 🚫 Cancel: ❌ Not allowed (seller)
  * 🚫 Withdraw: ❌ Not allowed

---

#### 3. `executed`

* **Meaning**: Seller marked service as delivered.
* **Entered by**: Seller execute the Service
* **Who can act**:

  * Buyer can confirm → `completed`
  * Buyer can dispute → `disputed`
  * Seller can withdraw after 5 days post-expiration (if no dispute submitted)
* **Transitions to**:

  * `completed` → when buyer complete service
  * `disputed` → when buyer dispute service
* **Permissions**:

  * 🚫 Rollback: ❌ Not allowed
  * ✅ Withdraw: ✅ Allowed (only 5 days after expiration)
  * 🚫 Cancel: ❌ Not allowed

---

#### 4. `disputed`

* **Meaning**: Buyer raised a dispute over execution/delivery.
* **Entered by**: Buyer dispute the service
* **Who can act**:

  * Buyer can complete it
  * Seller can cancel it
* **Transitions to**:

  * `Complete` → By Customer
  * `Cancel` → By Seller
* **Permissions**:

  * 🚫 Rollback: ❌ Not allowed
  * 🚫 Withdraw: ❌ Not allowed
  * 🚫 Cancel: ❌ Not allowed

---

#### 5. `completed`

* **Meaning**: Buyer confirmed that service was delivered and accepted.
* **Entered by**: Buyer complete the service
* **Who can act**:

  * Seller → can now withdraw
* **Permissions**:

  * 🚫 Rollback: ❌ Not allowed
  * ✅ Withdraw: ✅ Allowed (seller)
  * 🚫 Dispute: ❌ Not allowed
  * 🚫 Cancel: ❌ Not allowed

---

#### 6. `canceled`

* **Meaning**: Seller canceled the service before delivery or completion.
* **Entered by**: Seller calls `cancelService()`
* **Who can act**:

  * Buyer can rollback to retrieve funds
* **Permissions**:

  * ✅ Rollback: ✅ Allowed (buyer)
  * 🚫 Withdraw: ❌ Not allowed
  * 🚫 Execute/Complete: ❌ Not allowed

---

### 📌 Notes

* **Dispute only happens from `active` or `executed`**
* **Rollback only allowed when:**

  * State is not `active` or is expired
  * State is not `executed`, `completed`, or `disputed`
* **Withdraw only allowed when:**

  * State is `completed`
  * Or `executed` and no dispute submitted by customer and 5 days passed after expiretion day
* **No state transitions allowed from `completed`, `disputed`, or `canceled`** unless manually handled

> 🔐 Funds are locked until the customer approves service completion.

---

## 📂 6. Creating a Verifiable Presentation (VP)

Combine multiple VCs into a single presentation file.

### Steps:

1. Go to **“Credentials”** > Tap **“New Verifiable Entity”**.
2. Enter the **issuer DID** (your identity or a key-based DID).
3. Select VCs from your list.
4. Tap **“Create Presentation”** and sign.
5. The presentation is stored in your wallet and can be exported manually.

---

## 📦 7. Exporting and Sharing credentials

All credentials, presentations, and document references can be exported as JSON files.

### To Export:

1. Open the credentials page.
2. Tap **“Export”**, file will be created in **"Download"** folder in internal storage.

### Sharing Options:

* Share file manually via email or messaging apps.
* Upload to IPFS or Arweave for decentralized access (optional).
