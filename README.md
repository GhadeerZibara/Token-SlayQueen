

# ICP Crypto Token Project — SlayQueen

This project implements a cryptocurrency token called **SlayQueen**, built to run on the **Internet Computer (ICP) blockchain**.  
The token is implemented using **Motoko**, a programming language created by the DFINITY team specifically for writing smart contracts that run on ICP canisters.


> **Note:** This project is designed specifically for the ICP blockchain, so there is no live demo available.  
> You can explore the full codebase and run it locally using the DFX SDK if desired.


## Features

The SlayQueen token provides the following functionality:

- **Claim free tokens:** Each user can claim 10,000 SlayQueen (SQN) tokens once.  
- **Check balance:** Users can query their current token balance.  
- **Transfer tokens:** Users can transfer tokens to other accounts, with balances updated automatically.  

These features demonstrate core blockchain concepts such as token state management, transfers, and user-specific balances.

---

## Tech Stack

### Frontend
- **React**: Used to build the user interface, including components like `Faucet`, `Balance`, and `Transfer`.  
- **HTML & CSS**: Structure and styling for the frontend.  
  

### Backend
- **Motoko**: Implements the smart contract logic for the token.  
- **ICP Canisters**: Store the token state, handle transfers, and track balances.  
- **DFX SDK**: Used for local development and canister deployment.  

---

## main.mo Overview

The Motoko smart contract (`main.mo`) defines the core logic of the SlayQueen token:

- **Owner & Total Supply**: The token has an initial total supply (1,000,000,000 SQN) assigned to the owner.  
- **Balances**: Each user’s token balance is stored in a `HashMap`.  
- **Queries**:
  - `balanceOf(principal)` — Returns the token balance of a given user.  
  - `getSymbol()` — Returns the token symbol ("SQN").  
- **Shared Functions**:
  - `payOut()` — Allows a user to claim 10,000 SQN tokens once. If already claimed, returns `"Already Claimed"`.  
  - `transfer(to, amount)` — Transfers tokens to another account, updating balances. Returns `"Success"` or `"Insufficient Funds"`.  
- **Upgrade Functions**:
  - `preupgrade()` and `postupgrade()` — Save and restore balances during canister upgrades.  

> This contract ensures that balances are tracked accurately and that token transfers and claims are handled securely on the ICP blockchain.


## How it Works

The SlayQueen token project consists of a React frontend that interacts with the Motoko smart contract canister.  

### 1. App
The `App` component combines all other components: `Header`, `Faucet`, `Balance`, and `Transfer`.

### 2. Faucet
- Users can claim their free **10,000 SQN tokens** by clicking the “Gimme gimme” button.  
- Calls the `payOut()` function in the token canister.  
- Updates the user’s balance and disables the button to prevent multiple claims.  

### 3. Balance
- Users enter a Principal ID to check the token balance.  
- Calls the `balanceOf(principal)` function from the Motoko canister.  
- Displays the current balance along with the token symbol.  

### 4. Transfer
- Users can send tokens to other accounts by entering the recipient’s Principal ID and the amount.  
- Calls the `transfer(recipient, amount)` function in the canister.  
- Updates balances for both sender and recipient.  
- Displays feedback to indicate success or insufficient funds.

### Overall Flow
1. Claim free tokens using the Faucet component.  
2. Check account balances with the Balance component.  
3. Transfer tokens to other users via the Transfer component.  
4. Frontend communicates asynchronously with the canister to ensure accurate updates of token balances on the blockchain.

---

## Running Locally

To explore or test the token locally:

```bash
# Start the local Internet Computer replica
dfx start --background

# Deploy the token canister
dfx deploy

```

---

## License 
Copyright 2022 London App Brewery LTD (www.appbrewery.com)

Copyright 2026 Ghadeer Zibara

This project is licensed under the [Apache License 2.0]
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

Here is the TL;DR version of the above licence:
https://tldrlegal.com/license/apache-license-2.0-(apache-2.0)
