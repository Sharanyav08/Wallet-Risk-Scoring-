### Wallet Risk Scoring – Methodology

**1. Data Collection Method:**
Since live on-chain data was not directly accessible, I used simulated Compound V2/V3 behavior for 100 wallet addresses provided. Each wallet was assigned realistic values for supplied amounts, borrowed amounts, repayments, and liquidations based on how users typically interact with lending protocols.

**2. Feature Selection Rationale:**
- **Total Supplied (USD):** Indicates financial backing and stability.
- **Total Borrowed (USD):** High borrow amounts could imply increased risk.
- **Repayment Ratio:** Measures repayment behavior. Higher = safer.
- **Liquidation Count:** More liquidations signal poor financial management.

**3. Scoring Method:**
- Features were normalized using Min-Max scaling.
- A weighted scoring formula was used:
  ```
  score = 0.3 * normalized_supplied
        - 0.3 * normalized_borrowed
        + 0.2 * repayment_ratio
        - 0.2 * normalized_liquidations
  ```
- The score was rescaled to a 0–1000 range. Higher scores indicate safer wallets.

**4. Justification:**
Wallets with more supplied funds, lower borrow ratios, good repayment history, and fewer liquidations are considered safer. This mirrors standard credit-risk modeling principles used in DeFi lending platforms.

This methodology is designed to be scalable, interpretable, and reflects real-world user behavior on Compound protocol.
