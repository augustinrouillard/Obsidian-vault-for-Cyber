---
share: true
---
```markdown
# Note: Finding Ethereum Transactions with Etherscan

## How to Find a Transaction

- Use [https://etherscan.io/](https://etherscan.io/) to search for Ethereum transactions.
- You can search by:
  - **Transaction hash**
  - **Wallet address**
  - **Block number**
  - **Token or contract address**

## Viewing Transaction History

- On Etherscan, enter a wallet address in the search bar to view its full transaction history.
- You can see:
  - Incoming and outgoing transactions
  - Timestamps
  - Amounts
  - Related smart contracts

## Extra: Mining Pool Connection String

- If you need to check mining activity or connect to a mining pool, you might see a connection string like:

  ```
  stratum://ethwallet.workerid:password@miningpool:port
  ```

  - `ethwallet`: Your Ethereum wallet address
  - `workerid`: Worker name/ID
  - `password`: (optional) password for the worker
  - `miningpool`: Mining pool domain or IP
  - `port`: Port number

- You can use the wallet address from this string to look up its transactions on Etherscan.

---

**Summary:**  
Use [Etherscan](https://etherscan.io/) to search for and analyze Ethereum transactions by wallet address, transaction hash, or other identifiers.  
You can extract wallet addresses from mining pool connection strings to investigate their activity.

```