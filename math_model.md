# Mathematical Model
## General Finance Definition
* **Money**: an financial asset whose real worth is changing with the period
* **Period**: here, a period is an integer point in time where the saving's worth is evaluated.
  ```
  |  |  |  |  | ... |
  0  1  2  3  4 ... n
  ```
* **Future Value ($FV_{k}$)**: the future worth of a present sum of money at period k
* **Present Value ($PV$)**: the present worth of a future sum of money at period 0
$$
    FV_{0} = PV
$$
* **Interest Rate**: the rate (in decimal) that money changes its value with the period (could be positive, negative, or 0).
* **PMT**: money value of each payment to an account or contract

## Definition 1: Discrete Compounding

When an initial sum of money keeps growing through an interest gain and the interest gain generates more interest gains.

1. **Initial Value**
$$
    FV_{0} = PV
$$
2. **Growth $(k \geq 0)$**
$$
    FV_{k+1}=(FV_{k}) \times (1 + i)
$$


## Formula 1: Discrete Compounding
### Formula
Future Value of an Annually Compounding Present Value

$$
    FV_{n} = PV (1 + i)^n, \space n \geq 0
$$

### Observations
* This formula applies only if we put the money earned through interest back into savings
* Saving money might not be the best option because inflation is a negative interest that chips away savings
* At a fixed $n$ and $i$, $FV_{n}$ is proportional to the $PV$
* Given a future value at period $n$ with $i$, we can compute the present value

### Example
* If you save $100 today into the bank and earn interest of 10%, how much do you have in 3 years (assume no withdrawal)?

### Proof
We will show that this is true through the strong induction.

**Base Case**: At the end of period 0, we have

$$
    FV_{0} = PV (1 + i)^{0} = PV
$$

This is **true** from *Definition 1.1*.

**Inductive Hypothesis**:

$$
    FV_{k} = PV (1 + i)^{k}
$$

**Inductive Case**:

For the k + 1 case, at the end of period k + 1, we have

$$
    \begin{aligned}
    FV_{k + 1} &= PV (1 + i)^{k + 1} \\
    &= PV(1 + i)^{k} \times (1 + i) & \text{(Expanding the exponent)} \\
    &= (FV_{k}) \times (1 + i) & \text{(Inductive Hypothesis)} \\
    \end{aligned}
$$

This is **true** from *Definition 1.2*

Therefore, *Formula 1* is true.

## Definition 2: Annuity
1. **Initial Payment**
$$
    FV_{1} = PMT
$$
2. **Growth** ($k \geq 1$)
$$
    FV_{k+1} = (FV_{k}) \times (1 + i) + \text{PMT}\\ 
$$

* **Annuity**: a contract that requires regular payments for more than one full period to the person/account entitled to receive the payments.
The **first payment starts at period 1**.
* **Perpetuity**: an annuity with no end (infinite period)
## Formula 2: Future Value of an Annuity
### Formula 
Future value **at period n** of an annuity with PMT **starting at period 1**

$$
    FV_{n} = \frac{\text{PMT}}{i}\left[(1 + i)^n - 1\right],
    \space
    \space
    n \geq 1
$$

### Observations
* We can derive the following summation through the recurrence relations in *Definition 2*, then use the geometric series sum to derive *Formula 2*
$$
      FV_{n} = \sum_{k = 1}^{n} \text{PMT} (1 + i)^{k - 1} \\
      = \text{PMT} (1 + i)^{0} + \text{PMT} (1 + i)^{1} + \ldots + \text{PMT} (1 + i)^{n - 1}
$$

### Examples
* If you save $1000 a year for three years, starting at the end of the first year, how much do you have in three years?
* If you wanted to have $1,000,000 40 years from now (at n=40), how much do you have to save every year?

### Proof

Let's prove this formula with the strong induction.

**Base Case**: n = 1

$$
    FV_{1} = \frac{\text{PMT}}{i}\left[(1 + i) - 1\right] = \text{PMT}
$$

This is true by *Definition 2.2.1*

**Inductive Hypothesis**  
$$
    FV_{k} = \frac{\text{PMT}}{i}\left[(1 + i)^k - 1\right]
$$

**Inductive Case**:
$$
    \begin{aligned}
    FV_{k + 1}
    &= \frac{\text{PMT}}{i}\left[(1 + i)^{k+1} - 1\right] & \\
    &= \frac{\text{PMT}}{i}\left[(1 + i)^{k+1} - (1 + i) + i\right] & \\
    &= \frac{\text{PMT}}{i}\left[\left((1 + i)^{k} - 1\right)(1 + i) + i\right] & \\
    &= \frac{\text{PMT}}{i}\left[(1 + i)^{k} - 1\right](1 + i) + \text{PMT} & \\
    &= (FV_{k}) \times (1 + i) + \text{PMT} & \text{(Inductive Hypothesis)} \\
    \end{aligned}
$$

We know the inductive case is true by *Definition 2.2*

Therefore, *Formula 2* is true.

## Formula 3: Present Value of an n-year Annuity
### Formula

The present value of an n-year annuity with the first payment **starting at period 1** and the **last payment at period n**

$$
    PV = \frac{\text{PMT}}{i}\left[1 - \frac{1}{(1 + i)^n}\right],
    \space
    \space
    n \geq 1
$$

### Observations
* We can derive this formula by finding the present value of each payment then sum them to get the money's present value in total

$$
    PV = \sum_{k = 1}^{n} \text{PMT}\left(\frac{1}{1 + i}\right)^k \\
    = \left(\frac{1}{1 + i}\right)\left(\sum_{k = 1}^{n} \text{PMT}\left(\frac{1}{1 + i}\right)^{k - 1}\right)
$$

### Examples
### Proof

<!-- Inflation

-Keep money the same but change the price

At year 0, Present Price = Present Value
            
At year 1,
* Future price = Present price × (1 + inflation)
* $FV_{year=1} = PV$

FV/FP = 1/(1+inflation)

-Keep price the same but change the money

At year 0, Present Price = Present Value

At year 1, 
* Future price = Present price
* $FV_{year=1} = ?$

FV / PV = 1/(1 + inflation)
FV = PV/(1 + inflation) -->