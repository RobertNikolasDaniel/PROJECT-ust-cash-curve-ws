# PROJECT-cash-curve-ust-ws

Treasury curve and portfolio risk workstation focused on modeling the structural mechanics of cash U.S. Treasury exposure.

This project began as a simple duration and convexity calculator and gradually evolved into a multi-node Treasury portfolio analytics engine focused on:

- Yield curve structure
- DV01 normalization
- Convexity-adjusted pricing
- Portfolio risk aggregation
- Curve steepening and flattening mechanics
- Funding-adjusted carry
- Relative value intuition across Treasury maturities

The purpose of this project was not to recreate institutional infrastructure, but instead to build a clean and transparent educational framework that demonstrates Treasury portfolio mechanics in a visually intuitive way.

---

# Core Concepts Modeled

## Treasury Yield Curve

The workstation models a simplified Treasury curve across:

- 2Y
- 5Y
- 7Y
- 10Y
- 20Y
- 30Y

Users can apply custom basis point shocks to individual maturities in order to observe:

- Parallel shifts
- Steepeners
- Flatteners
- Twist scenarios
- Portfolio-level risk outcomes

---

# Duration and Convexity Pricing

Bond prices are adjusted using a modified duration and convexity approximation:

\[
P_{new}
=
P_0
\left(
1
-
D_{mod}\Delta y
+
\frac12 C(\Delta y)^2
\right)
\]

Where:

- \(P_0\) = initial bond price
- \(D_{mod}\) = modified duration
- \(C\) = convexity
- \(\Delta y\) = yield shock in decimal form

This allows the workstation to estimate nonlinear bond price behavior under changing rate environments.

---

# Local Post-Shock DV01

Rather than keeping DV01 static after a rate move, the project estimates a new local modified duration after the shock:

\[
Mod_{new}
=
Mod_{old}
-
Convexity \times \Delta y
\]

This updated local duration is then used to estimate post-shock DV01:

\[
DV01
=
\frac{
Price \times Mod \times Notional
}{
100 \times 10000
}
\]

This allows the system to demonstrate how Treasury sensitivity itself changes after rate moves due to convexity effects.

---

# Portfolio Analytics

The workstation aggregates Treasury exposure into portfolio-level metrics:

- Total Notional
- Total DV01
- Total Shock P/L
- Total Carry
- Total Return

Where:

\[
TotalReturn
=
ShockPnL
+
Carry
\]

This separates:

- mark-to-market risk
- financing economics
- portfolio exposure
- duration sensitivity

into independent structural dimensions.

---

# Carry Engine

One of the primary focuses of the project was distinguishing between:

- headline yield
- actual economic carry

Carry is estimated using:

\[
Carry
=
(Yield - FundingRate)
\times
Notional
\times
\frac{DaysHeld}{365}
\]

This demonstrates how financing conditions can materially alter Treasury portfolio economics even when yield remains unchanged.

The project intentionally emphasizes carry over raw yield as a more meaningful representation of financed portfolio exposure.

---

# DV01 Hedge Ratios

The workstation also calculates simplified DV01-neutral hedge ratios across Treasury maturities.

Examples include:

- 2s5s
- 2s10s
- 5s30s
- 10s30s

Using:

\[
HedgeRatio
=
\frac{
LongerMaturityDV01
}{
ShorterMaturityDV01
}
\]

This visually demonstrates how duration risk scales nonlinearly across the curve.

---

# Design Philosophy

This project intentionally avoids excessive infrastructure complexity such as:

- full coupon schedule modeling
- bootstrapping
- spline interpolation
- repo specialness
- accrued interest mechanics
- settlement convention logic

The focus instead is:

> simple, honest, useful Treasury risk intuition

The workstation was designed to remain:

- visually interpretable
- mathematically transparent
- educationally intuitive
- modular and extensible

while still capturing many of the core structural relationships present in Treasury portfolio risk management.

---

# Purpose

This project was built independently as part of a broader effort to study:

- fixed income markets
- Treasury relative value
- duration risk
- yield curve structure
- financing economics
- portfolio sensitivity mechanics

through direct systems building and modeling.
