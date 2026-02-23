# OTC Derivatives Margining & Liquidity Risk  
### A Monte Carlo Simulation Study

## 📌 Project Overview

This project analyzes margining practices in non-centrally cleared OTC derivatives using a Monte Carlo simulation framework. The objective is to examine the interaction between counterparty credit risk, liquidity constraints, and systemic risk under different regulatory policies.

The simulation runs 10,000 price paths over a 252-day horizon to evaluate how Initial Margin (IM), Variation Margin (VM), Margin Period of Risk (MPOR), and collateral rules impact both counterparties.

---

## 🏗 Economic Setup

Two institutions enter a forward contract:

### Institution A (Investor)
- Long forward position
- Liquidity constrained
- Holds limited cash and illiquid assets
- Can default due to:
  - Exogenous shock
  - Liquidity shortage (in augmented model)

### Institution B (Dealer)
- Takes opposite position
- Unlimited liquidity
- Does not default

The mark-to-market (MTM) value is:

V_t = Q (S_t - K)

Price dynamics:

S_{t+Δ} - S_t ~ N(0, Δσ²)

---

## 💰 Margin Framework

### Initial Margin (IM)
- One-sided 99% VaR over the MPOR (10 days)
- Posted upfront by Investor A
- Formula:

IM = z × Q × σ × √MPOR

### Variation Margin (VM)
- Exchanged daily
- Resets collateral to current MTM
- Drives ongoing liquidity needs

---

## 🔥 Augmented Model: Fire Sales & Liquidity Defaults

Investor A holds:
- Initial cash (L₀)
- Illiquid assets (A₀)

If VM calls exceed available cash:
- Illiquid assets must be sold at discount (fire-sale haircut)
- If both cash and assets are exhausted → liquidity-driven default

This introduces endogenous liquidity risk into the system.

---

## 📊 Simulation Structure

- 10,000 Monte Carlo paths
- 252 trading days
- Default intensity calibrated from annual PD
- Loss distribution computed for Dealer B
- Fire-sale costs tracked for Investor A

Outputs include:
- Loss frequency
- Mean loss
- 99th percentile (tail risk)
- Default breakdown
- Total fire-sale costs

---

## 🔎 Policy Experiments

The model evaluates several regulatory scenarios:

### 1️⃣ Increase in Initial Margin
- IM multiplier k applied to baseline VaR
- Higher IM reduces Dealer B's credit risk
- No impact on liquidity-driven defaults

### 2️⃣ VM Frequency Change
- Daily vs weekly exchange
- Less frequent VM increases uncollateralized exposure

### 3️⃣ MPOR Reduction
- Shorter liquidation window reduces required IM
- Improves close-out efficiency

### 4️⃣ Collateral Expansion
- Illiquid assets allowed as VM collateral
- Eliminates fire-sale contagion
- Transfers severe tail risk to Dealer B

---

## ⚖ Key Findings

- IM is highly effective in eliminating dealer credit losses.
- Higher IM does not reduce liquidity stress for Investor A.
- Fire sales are driven by daily VM volatility, not IM size.
- Expanding collateral eligibility reduces market-wide fire sales but dramatically increases dealer tail risk.
- Margin policy alone is insufficient for systemic stability.

---

## 🧠 Conclusion

The study highlights a structural trade-off in OTC margining:

Protecting dealers via stricter margin requirements does not solve liquidity fragility for investors. Conversely, relaxing collateral rules reduces contagion but concentrates catastrophic tail risk on dealers.

Sustainable systemic stability requires:
- Robust, haircut-adjusted margin frameworks
- Volatility-scaled liquidity buffers
- Careful calibration of MPOR and collateral eligibility

---

## 🛠 Technologies Used

- Python
- NumPy
- Monte Carlo Simulation
- Quantitative Risk Modeling
- Value-at-Risk (VaR) Framework

---

## 📈 Topics Covered

Quantitative Finance · Risk Management · Derivatives · Monte Carlo Simulation · Systemic Risk · Liquidity Risk · Margining · Financial Stability
