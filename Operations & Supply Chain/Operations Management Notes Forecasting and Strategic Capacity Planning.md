# Operations Management: Forecasting and Strategic Capacity Planning

Exam-oriented notes with explanations, formulas, worked examples and practice Q&A, based on Dr. Radha Mohan Gupta's slides.

## Part 1: Forecasting

### 1.1 What is a forecast?

A **forecast** is a statement about the future value of a variable of interest: demand, weather, resource availability, prices and so on. In operations, we mostly forecast **demand**, because almost every other plan (production, staffing, inventory, purchasing, capacity) is built on it. A forecast is never perfect, so good planning also needs an estimate of **how wrong the forecast might be** (that is what the error measures in section 1.10 are for).

### 1.2 Strategic role of demand forecasting

- **Guides supply chain planning and operations**: how much to produce, buy and ship, and when.
- **Reduces uncertainty in decision-making**: decisions rest on evidence rather than guesses.
- **Supports budgeting and financial planning**: expected sales drive revenue and cost budgets.
- **Manages inventory and avoids stockouts**: too high a forecast means excess stock; too low means lost sales.
- **Aids capacity planning and resource allocation**: long-term demand forecasts are converted into equipment, space and workforce needs (this links Part 1 to Part 2).

### 1.3 Components of demand

Actual demand is usually a mix of several patterns layered together (Figure 4.1 in the slides shows the actual demand line wiggling around a rising trend with seasonal peaks).

| Component | Meaning | Typical duration | Example |
| --- | --- | --- | --- |
| **Historical** | Past sales data used to identify patterns | n/a (it is the raw data) | Last 3 years of monthly sales |
| **Trend** | Persistent long-term upward or downward movement, caused by population, technology, income, culture | Several years | Growing demand for EVs |
| **Seasonal** | Regular up-and-down pattern tied to the calendar or time of day | Within one year (or within a week/day) | Ice cream in summer, festival sales |
| **Cyclical** | Wave-like variation linked to business cycle, economy, politics | More than one year (multiple years) | Housing boom and bust |
| **Irregular** | Caused by unusual, one-off events | Short, non-repeating | Strike, flood, pandemic lockdown |
| **Random** | Residual noise left after all other patterns are removed | Short, erratic | Unexplained day-to-day variation |

**Trend vs seasonal vs cyclical (a favourite exam question):**

- Seasonal repeats at a **fixed, known period** within a year; cyclical has **no fixed length** and spans more than a year.
- Cyclical patterns are driven by economic or political conditions and are often explained by **causal (associative)** relationships.
- Trend is a steady drift; seasonal and cyclical are oscillations around that drift.

**Seasonality lengths (from the slide):**

| Period length | Season length | Number of seasons in pattern |
| --- | --- | --- |
| Week | Day | 7 |
| Month | Week | 4 to 4.5 |
| Month | Day | 28 to 31 |
| Year | Quarter | 4 |
| Year | Month | 12 |
| Year | Week | 52 |

Read it as: if the pattern repeats every year and you collect monthly data, you have 12 seasons per pattern.

### 1.4 Elements of a good forecast

A good forecast should be **timely** (available in time to act), **accurate** (and the degree of accuracy should be stated), **reliable** (works consistently), **expressed in meaningful units** (units or rupees that planners use), **in writing** (so everyone works from the same numbers and it can be checked later), **simple to understand and use**, and **cost-effective** (benefit exceeds cost).

### 1.5 Steps in the forecasting process

1. **Determine the purpose** of the forecast (what decision will it support? how detailed?).
2. **Establish a time horizon** (short, medium or long term; accuracy falls as the horizon lengthens).
3. **Obtain, clean and analyse appropriate data** (remove errors and one-off distortions).
4. **Select a forecasting technique** (depends on data available, horizon, cost, accuracy needed).
5. **Make the forecast.**
6. **Monitor the forecast errors** (if errors go beyond acceptable bounds, revisit the technique or parameters).

### 1.6 Forecasting approaches

**Qualitative (judgemental)** techniques use soft information: human factors, personal opinions, hunches. These are hard or impossible to quantify. Best when there is **no historical data** (new products) or when conditions have changed sharply.

**Quantitative** techniques rely on hard data and come in two families:

- **Time-series (projection) methods**: project patterns in past data into the future (naive, moving average, exponential smoothing).
- **Associative (causal) methods**: use explanatory variables to predict demand (for example regression of sales on price or advertising spend).

### 1.7 Qualitative techniques

- **Executive opinion**: a small group of senior managers meets and develops a forecast together. Fast and uses broad experience, but can be dominated by powerful personalities (groupthink).
- **Sales force opinion**: salespeople and customer service staff are close to customers and know their plans. Useful, but can be biased (optimism, or deliberately low estimates to make quotas easy).
- **Consumer surveys**: customers ultimately determine demand, so ask a sample of them. Direct, but costly, and stated intentions do not always become purchases.
- **Other approaches**: managers consult other managers, staff or outside experts.

**Delphi method (in depth)**

A structured, iterative process to reach a **consensus among experts** without them meeting face-to-face, which reduces the influence of dominant individuals.

1. A **facilitator** sends a questionnaire to a panel of experts.
2. Responses are **collected, summarised and shared anonymously**.
3. Experts **review the summary and revise** their answers in further rounds.
4. Iteration continues until responses **converge** to a consensus.

Use it when historical data is unavailable or unreliable. Common in **new product forecasting, policy formulation and long-term planning**. Strength: anonymity avoids bandwagon effects. Weakness: slow and time-consuming.

### 1.8 Time-series forecasting techniques

A **time series** is a time-ordered sequence of observations taken at regular intervals. The core assumption: **future values can be estimated from past values**.

#### (a) Naive forecast

The forecast for the next period equals the actual value of the previous period.

**F(t+1) = A(t)**

Simplest and cheapest method; it is also a benchmark that any fancier method should beat. It can be adapted for trend (add the last change) or seasonality (use the same period last year).

#### Averaging techniques (moving average, weighted moving average, exponential smoothing)

These work best when the series **varies around a stable average**. Averaging **smooths out** random fluctuations and can follow step changes or gradual level shifts. They lag behind when there is a strong trend.

#### (b) Simple moving average (MA)

Averages the **n most recent** actual values.

**F(t) = MA(n) = (A(t-1) + A(t-2) + ... + A(t-n)) / n**

where n is the number of periods in the average and A(t-i) is the actual value i periods ago.

- When new data arrives, **add the newest value and drop the oldest**, then recompute.
- The choice of **n sets the sensitivity**: fewer periods means more **responsive** (follows changes quickly but is noisy); more periods means **smoother** but slower to react.

#### (c) Weighted moving average (WMA)

Same idea, but recent values get **more weight**.

**F(t) = w1 x A(t-1) + w2 x A(t-2) + ... + wn x A(t-n)**

The weights must **sum to 1** (100%). Choosing them is somewhat arbitrary and involves trial and error.

#### (d) Simple exponential smoothing

A weighted average method: new forecast = **previous forecast plus a percentage of the forecast error**.

**F(t) = F(t-1) + α x (A(t-1) - F(t-1))**

where F(t) is the forecast for period t, F(t-1) the previous forecast, A(t-1) the previous actual, and α (alpha) the smoothing constant, between 0 and 1.

Equivalent form: **F(t) = α x A(t-1) + (1 - α) x F(t-1)**

**Understanding α:**

- **High α (say 0.7 to 0.9)**: reacts quickly to recent changes, little smoothing; good when demand shifts a lot.
- **Low α (say 0.05 to 0.3)**: heavy smoothing, slow to react; good for stable demand with random noise.
- Weights given to older data **decline exponentially**, which is where the name comes from. Unlike a moving average, you only need the last forecast, the last actual and α (no long data history to store).
- To start the series, a common choice is to set the first forecast equal to the first actual (or the average of a few initial values).

**Comparison of the techniques**

| Technique | Uses | Strength | Weakness |
| --- | --- | --- | --- |
| Naive | Last value only | Trivial, cheap, benchmark | Passes on all random noise |
| Moving average | Last n values, equal weights | Easy; n controls smoothness | Needs n data points stored; lags trends; ignores older data entirely |
| Weighted MA | Last n values, unequal weights | Emphasises recent data | Weights chosen by trial and error |
| Exponential smoothing | Previous forecast and actual | Minimal data needed; α is tunable | Lags trend; α must be chosen |

### 1.9 Worked example (same data, three methods)

Weekly demand: **Week 1 to 6 = 100, 110, 120, 115, 125, 130.** Forecast Week 7.

**3-week moving average:** (115 + 125 + 130) / 3 = 370 / 3 = **123.33**

**Weighted moving average** with weights 0.5 (latest), 0.3, 0.2: 0.5(130) + 0.3(125) + 0.2(115) = 65 + 37.5 + 23 = **125.5**

**Exponential smoothing, α = 0.2**, starting with F1 = 100 (= A1):

| Week | Actual | Forecast | Calculation |
| --- | --- | --- | --- |
| 1 | 100 | 100.00 | starting value |
| 2 | 110 | 100.00 | 100 + 0.2(100 - 100) |
| 3 | 120 | 102.00 | 100 + 0.2(110 - 100) |
| 4 | 115 | 105.60 | 102 + 0.2(120 - 102) |
| 5 | 125 | 107.48 | 105.6 + 0.2(115 - 105.6) |
| 6 | 130 | 110.98 | 107.48 + 0.2(125 - 107.48) |
| 7 | ? | **114.79** | 110.984 + 0.2(130 - 110.984) |

**Observation:** demand is trending upward, so exponential smoothing with a small α (114.79) lags far behind the latest values, while the WMA (125.5) tracks them closely. This is why averaging methods are meant for series that **vary about an average**, not strongly trending ones.

### 1.10 Forecast accuracy and control

Forecasts will have errors, so we (i) allow for them in planning and (ii) **monitor** them. If errors stray beyond acceptable bounds, corrective action is needed (change the method, the α, or the n).

**Error = Actual - Forecast = A - F**

Positive error means the forecast was too low (under-forecast); negative means too high (over-forecast).

| Measure | Formula | What it tells you |
| --- | --- | --- |
| **MAD** (Mean Absolute Deviation) | Σ\|A - F\| / n | Average size of the error, in the **same units** as the data. Weights all errors evenly. |
| **MSE** (Mean Squared Error) | Σ(A - F)² / n (the slide divides by n - 1) | Squares the errors, so **large errors are penalised heavily**. Units are squared. |
| **MAPE** (Mean Absolute Percent Error) | Σ(\|A - F\| / A x 100) / n | Error as a **percentage of actual**: relative error, unit-free, good for comparing across products. |
| **MFE** (Mean Forecast Error, or bias) | Σ(A - F) / n | Average signed error. Near zero means no systematic **bias**; positive means consistently under-forecasting, negative means over-forecasting. Positive and negative errors cancel, so it shows bias, not accuracy. |

**Slide example (n = 5):**

| Period | Actual (A) | Forecast (F) | Error (A - F) | \|Error\| | Error² | \|Error\|/A x 100 |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 107 | 110 | -3 | 3 | 9 | 2.80% |
| 2 | 125 | 121 | 4 | 4 | 16 | 3.20% |
| 3 | 115 | 112 | 3 | 3 | 9 | 2.61% |
| 4 | 118 | 120 | -2 | 2 | 4 | 1.69% |
| 5 | 108 | 109 | 1 | 1 | 1 | 0.93% |
| **Sum** |  |  | 3 | **13** | **39** | **11.23%** |

- **MAD** = 13 / 5 = **2.6**
- **MSE** = 39 / (n - 1) = 39 / 4 = **9.75** (dividing by n instead would give 7.8; follow whatever your instructor uses, the slide uses n - 1)
- **MAPE** = 11.23% / 5 = **2.25%**
- **MFE** = 3 / 5 = **0.6** (a slight tendency to under-forecast)

**Which to use?** MAD is easiest to interpret; MSE when big misses are especially costly; MAPE when comparing forecasts of items on different scales; MFE to check for bias. A lower value on the same data means a better method.

### 1.11 Quick revision: Forecasting

- Components: historical, trend, seasonal, cyclical (plus irregular and random).
- Qualitative: executive opinion, sales force, consumer survey, Delphi. Quantitative: naive, MA, WMA, exponential smoothing (time-series) and regression (associative).
- Smaller n or larger α = more responsive; larger n or smaller α = smoother.
- Error = A - F. MAD, MSE, MAPE measure accuracy; MFE measures bias.

### 1.12 Practice Q&A: Forecasting

**Q1. Define forecasting and explain its strategic role in operations.**

*A.* A forecast is a statement about the future value of a variable of interest, typically demand. Its strategic role: it guides supply chain planning, reduces uncertainty, supports budgeting, helps manage inventory and avoid stockouts, and feeds capacity planning and resource allocation.

**Q2. Differentiate between seasonal and cyclical components of demand.**

*A.* Seasonal variation is a regular, repeating pattern within a year (or week/day) tied to the calendar, with a fixed and known length, such as festival-season sales. Cyclical variation is a wave-like movement lasting more than one year with no fixed length, driven by economic or political conditions, such as a recession and recovery.

**Q3. Explain the Delphi method and state when it is useful.**

*A.* A facilitator circulates a questionnaire to a panel of experts who stay anonymous and never meet. Responses are summarised and fed back, experts revise their views, and rounds repeat until opinions converge. It is useful when historical data is missing or uncertain: new product forecasts, policy formulation, long-term planning. Anonymity prevents dominant individuals from steering the group.

**Q4. Sales for the last three weeks were 52, 58 and 55 units. Using a 3-week moving average, what is the forecast for next week? Then use weights 0.5, 0.3, 0.2 (latest first).**

*A.* MA = (52 + 58 + 55) / 3 = **55**. WMA = 0.5(55) + 0.3(58) + 0.2(52) = 27.5 + 17.4 + 10.4 = **55.3**.

**Q5. The forecast for last month was 200 units and actual demand was 220. With α = 0.3, what is this month's forecast?**

*A.* F = 200 + 0.3(220 - 200) = 200 + 6 = **206 units**.

**Q6. What happens to an exponential smoothing forecast if α is set to 1? What if α is close to 0?**

*A.* With α = 1, F(t) = A(t-1): it becomes the naive forecast (fully reactive, no smoothing). With α near 0, the forecast barely changes from the previous forecast (very smooth, very slow to react).

**Q7. Actual demand for three periods was 50, 55, 52 and the forecasts were 48, 56, 50. Compute MAD, MSE (divide by n), MAPE and MFE.**

*A.* Errors: +2, -1, +2.

- MAD = (2 + 1 + 2) / 3 = **1.67**
- MSE = (4 + 1 + 4) / 3 = **3.0**
- MAPE = (2/50 + 1/55 + 2/52) x 100 / 3 = (4% + 1.82% + 3.85%) / 3 = **3.22%**
- MFE = (2 - 1 + 2) / 3 = **1.0** (slight under-forecasting)

**Q8. Why can MFE be near zero even when forecasts are poor? Which measure would you add?**

*A.* Over- and under-forecasts cancel out in a signed average, so MFE detects bias but not accuracy. Add MAD, MSE or MAPE, which use absolute or squared errors.

**Q9. Why do moving averages and exponential smoothing perform poorly on a strongly trending series?**

*A.* They average past values, all lower (or all higher) than the current level, so the forecast consistently lags the trend. Use trend-adjusted methods, or associative methods like regression.

**Q10. List the steps in the forecasting process.**

*A.* Determine the purpose; establish the time horizon; obtain, clean and analyse data; select a technique; make the forecast; monitor the forecast errors.

## Part 2: Strategic Capacity Planning

### 2.1 What is capacity?

**Capacity** is the upper limit or ceiling on the load that an operating unit can handle (a machine, a plant, a hospital, a call centre). Capacity needs cover **equipment, space and employee skills**.

**Goal of capacity planning:** to achieve a **match between the long-term supply capabilities of an organisation and the predicted level of long-term demand.**

- **Overcapacity** means operating costs that are too high (idle machines and staff still cost money).
- **Undercapacity** means strained resources and possible loss of customers (unmet demand goes to competitors).

### 2.2 Key questions in capacity planning

- **What** kind of capacity is needed?
- **How much** is needed to match demand?
- **When** is it needed?

Related questions: How much will it cost? What are the benefits and risks? Are there sustainability issues? Should capacity change all at once or in several smaller steps? Can the supply chain handle the changes (suppliers, logistics)?

### 2.3 Why capacity decisions are strategic

Capacity decisions: (1) affect the ability to meet future demand; (2) affect operating costs; (3) are a major determinant of initial cost; (4) often commit resources for the long term, so they are hard to reverse; (5) affect competitiveness; (6) affect ease of management; (7) have become more complex due to globalisation; and (8) must be planned in advance because they consume large financial and other resources.

### 2.4 Defining and measuring capacity

Measure capacity in **units that do not require updating** (units per day, seats, beds, machine hours). Measuring in **dollars is problematic** because prices, costs and exchange rates keep changing, so the number would need constant revision even though the physical capacity has not changed.

Two useful definitions:

- **Design capacity**: the **maximum** output rate an operation, process or facility is **designed** for (the ideal).
- **Effective capacity**: design capacity **minus allowances** such as personal time, maintenance, scheduling conflicts, changeovers (the realistic ceiling).
- **Actual output**: the rate of output **actually achieved**. It cannot exceed effective capacity.

Ordering: **Actual output ≤ Effective capacity ≤ Design capacity**

**System effectiveness measures (both expressed as percentages):**

**Efficiency = Actual output / Effective capacity**

**Utilisation = Actual output / Design capacity**

Efficiency asks: how well are we doing against what we can realistically do? Utilisation asks: how much of the ideal maximum are we using?

**Slide example:** Design capacity = 50 trucks/day, effective capacity = 40 trucks/day, actual output = 36 trucks/day.

- Efficiency = 36 / 40 = **90%**
- Utilisation = 36 / 50 = **72%**

### 2.5 Determinants of effective capacity

- **Facilities**: size, layout, location, work environment.
- **Product and service factors**: design, product mix (a varied mix lowers capacity due to changeovers).
- **Process factors**: process capability, quality (rework consumes capacity).
- **Human factors**: skills, training, motivation, absenteeism, experience.
- **Policy factors**: overtime rules, number of shifts, working hours.
- **Operational factors**: scheduling, materials handling, inventory management, equipment breakdowns.
- **Supply chain factors**: supplier reliability, logistics, the capacity of upstream and downstream partners.
- **External factors**: regulations, safety standards, pollution limits.

### 2.6 Capacity strategies

Strategy formulation rests on assumptions and predictions about **long-term demand patterns, technological change and competitor behaviour**.

| Strategy | When capacity is added | Advantage | Risk |
| --- | --- | --- | --- |
| **Leading** | **Ahead** of expected demand increases | Meets demand without stockouts, can win market share, preempts competitors | Risk of overcapacity and idle cost if demand does not arrive |
| **Following** | **After** demand already exceeds current capacity | Low risk of excess capacity, higher utilisation | Possible lost sales and customers while waiting |
| **Tracking** | Similar to following, but in **small increments** to keep pace with demand | Smooth, low risk, steady match between supply and demand | Needs flexibility; small increments may cost more per unit |

### 2.7 Capacity cushion

**Capacity cushion** = extra capacity held to offset demand uncertainty.

**Capacity cushion = 100% - Utilisation**

In the truck example, utilisation was 72%, so the cushion is **28%**.

- Organisations with **greater demand uncertainty** typically hold a **larger** cushion (for example emergency services, fashion retailers).
- Organisations with **standard products and services** and predictable demand generally hold a **smaller** cushion.

### 2.8 Steps in capacity planning

1. **Estimate future capacity requirements.**
2. **Evaluate existing capacity and facilities** and identify gaps.
3. **Identify alternatives** for meeting the requirements.
4. **Conduct financial analyses** of each alternative.
5. **Assess key qualitative issues** (flexibility, public opinion, strategy fit).
6. **Select the best alternative** for the long term.
7. **Implement** the alternative chosen.
8. **Monitor results.**

### 2.9 Forecasting capacity requirements

- **Long-term** considerations concern the **overall level** of capacity needed. They require forecasting demand over a time horizon (this is where Part 1 is used) and converting that demand into capacity requirements.
- **Short-term** considerations concern **probable variations** in requirements. Here seasonal and other variations from the average matter more than long-term cycles and trends.

#### Calculating processing requirements

You need three inputs: a reasonably accurate **demand forecast**, **standard processing times**, and **available work time**.

**N = Σ (D(i) x p(i)) / T**, summed over products i = 1 to k

where N = number of machines (or workers) required, D(i) = forecast demand for product i in the planning horizon, p(i) = standard processing time per unit of product i, and T = processing time available per machine over the planning horizon.

In words: **total work hours required divided by hours one machine can provide**. Round **up** to a whole number of machines.

**Example:** Each machine is available 2,000 hours per year. Demand and processing times: Product A 20,000 units at 0.10 hr; Product B 12,000 units at 0.20 hr; Product C 5,000 units at 0.30 hr.

- Hours required = 20,000(0.10) + 12,000(0.20) + 5,000(0.30) = 2,000 + 2,400 + 1,500 = 5,900 hours
- N = 5,900 / 2,000 = 2.95, so **3 machines** are needed.

### 2.10 Service capacity planning

Services are harder to plan than manufacturing because of:

- **The need to be near customers**: the service is delivered where the customer is, so capacity must be spread across locations; convenience matters.
- **The inability to store services**: unlike goods, an unused seat, hour or appointment cannot be saved for later. Capacity must be present when the demand occurs.
- **Demand volatility**: the volume and timing of demand fluctuate (hour of day, day of week), and the time needed per customer varies.

#### Demand management strategies

Tactics to offset capacity limits and bring supply and demand closer: **pricing, promotions, discounts**, and other actions to **shift demand from peak to slow periods**. Examples: off-peak electricity tariffs, early-bird restaurant menus, weekday movie discounts.

### 2.11 In-house or outsource?

Once requirements are known, decide whether to **produce the good or service in-house or outsource**. Factors: **available capacity, expertise, quality considerations, the nature of demand** (steady demand favours in-house; erratic or peak demand favours outsourcing), **cost, and risks** (dependence on suppliers, loss of control, confidentiality).

### 2.12 Developing capacity strategies

- **Design flexibility into systems**: it is easier to add capacity if it was planned for (extra space, modular equipment).
- **Take the stage of the life cycle into account**: growth stage calls for expansion, decline for reduction.
- **Take a big-picture approach**: changes in one area affect the whole system, including suppliers and customers.
- **Prepare to deal with capacity chunks**: capacity often comes in lumps (you cannot buy half a machine), which creates temporary over or under capacity.
- **Attempt to smooth capacity requirements**: for example use complementary products with opposite seasonal peaks.
- **Identify the optimal operating level**: the output rate where average unit cost is lowest (section 2.14).
- **Choose a strategy if expansion is involved**: leading, following or tracking.

### 2.13 Bottleneck operation

A **bottleneck** is an operation in a sequence of operations whose capacity is **lower than that of the other operations**; it limits the output of the whole system, like the narrow neck of a bottle.

Slide figure: four operations each feed 10 units/hr, so 40 units/hr arrive at a bottleneck operation that can process only 30 units/hr. System output is capped at **30 units/hr**, and the excess piles up as waiting work. Adding capacity to any other operation does **nothing** for total output; only relieving the bottleneck raises it (and then the next-slowest step becomes the bottleneck).

### 2.14 Optimal operating level, economies and diseconomies of scale

Plot **average cost per unit** against **rate of output**: the curve is U-shaped. The bottom of the U is the **minimum cost point**, at the **optimal output rate**.

- **Economies of scale**: below the optimal level, raising output **lowers** average cost per unit. Reasons: fixed costs are spread over more units; construction costs rise at a decreasing rate as facility size grows (a double-size plant costs less than double); processing costs fall through standardisation.
- **Diseconomies of scale**: above the optimal level, raising output **raises** average cost per unit. Reasons: distribution costs rise (traffic congestion, shipping from one central facility instead of several smaller ones); complexity increases costs; inflexibility; extra layers of bureaucracy.

**Facility size and optimal level:** each plant size (small, medium, large) has its **own** U-shaped cost curve. Larger plants have a lower minimum cost and a higher optimal output rate, but only if demand can fill them. The minimum cost and optimal rate are functions of the size of the production unit.

### 2.15 Constraint management

A **constraint** is anything that limits a process or system from achieving its goals. Categories: **market** (not enough demand), **resource** (equipment, labour), **material** (shortages of inputs), **financial** (funding limits), **knowledge or competency** (missing skills), and **policy** (rules or procedures).

**Resolving constraints (five steps):**

1. Identify the **most pressing** constraint.
2. Change the operation to get **maximum benefit given the constraint**.
3. Make sure other parts of the process **support** the constraint (for example keep the bottleneck always busy).
4. **Explore and evaluate ways to overcome** the constraint.
5. **Repeat** until constraint levels are acceptable.

### 2.16 Evaluating capacity alternatives

Alternatives are judged from several perspectives.

- **Economic**: Is it feasible? How much will it cost? How soon can we have it? What are the operating and maintenance costs? What is its useful life? Is it compatible with present people and operations?
- **Non-economic**: for example **public opinion** (a plant closing or opening affects the community), environment, strategic fit.

**Techniques:** cost-volume analysis, financial analysis, decision theory (choose under uncertainty using probabilities and payoffs), waiting-line analysis (queueing: trade-off between server cost and customer waiting), and simulation (model the system on a computer).

### 2.17 Cost-volume analysis (break-even)

Focuses on the relationship between **cost, revenue and volume of output**.

- **Fixed costs (FC)**: constant regardless of output (rent, equipment, salaried staff).
- **Variable costs (VC)**: vary directly with output. **VC = Q x v**, where Q is quantity and v is variable cost per unit.
- **Total cost: TC = FC + VC = FC + v x Q**
- **Total revenue: TR = R x Q**, where R is revenue per unit.
- **Profit: P = TR - TC = R x Q - (FC + v x Q) = Q(R - v) - FC**

**Break-even point (BEP)** is the volume where total cost equals total revenue (profit is zero):

**Q(BEP) = FC / (R - v)**

The term **(R - v)** is the **contribution margin per unit**: each unit sold contributes this much toward covering fixed costs. Below Q(BEP) there is a loss; above it, profit. Related forms:

- Revenue at break-even = Q(BEP) x R
- **Volume for a target profit**: Q = (FC + target profit) / (R - v)

**Worked example:** FC = 60,000; v = 20; R = 50.

- Contribution = 50 - 20 = 30
- Q(BEP) = 60,000 / 30 = **2,000 units**, revenue at BEP = 2,000 x 50 = **100,000**
- Profit at 3,000 units = 3,000(30) - 60,000 = **30,000**
- Volume for 45,000 profit = (60,000 + 45,000) / 30 = **3,500 units**

**Point of indifference for two alternatives:** the volume at which two options have equal total cost (or equal profit). For options A and B: FC(A) + v(A) Q = FC(B) + v(B) Q, so **Q = (FC(A) - FC(B)) / (v(B) - v(A))**. Below that volume the option with lower fixed cost wins; above it the option with lower variable cost wins.

**Step costs and multiple break-even points:** capacity often comes in chunks (1 machine, 2 machines, 3 machines), so fixed cost **jumps stepwise** as volume capacity increases. The total cost line then has jumps, and the revenue line can cross it more than once, giving **multiple break-even quantities**.

**Assumptions of cost-volume analysis:**

- One product is involved.
- Everything produced can be sold.
- Variable cost per unit is the same at all volumes.
- Fixed costs do not change with volume (or change only in steps).
- Revenue per unit is the same at all volumes.
- Revenue per unit exceeds variable cost per unit.

### 2.18 Financial analysis

- **Cash flow**: the difference between cash received (from sales and other sources) and cash paid out (labour, material, overhead, taxes).
- **Present value (PV)**: the sum, in **current value**, of all future cash flows of an investment proposal. A rupee or dollar received later is worth less than one today because it could be invested meanwhile, so future cash flows are **discounted**.

**PV = CF(t) / (1 + r)^t**, summed over all periods; **NPV = PV of inflows - initial investment**

where r is the discount rate and t is the number of periods. An investment with **NPV > 0** is financially attractive; when comparing alternatives, prefer the higher NPV.

### 2.19 Quick revision: Capacity planning

- Actual ≤ Effective ≤ Design. Efficiency = Actual / Effective; Utilisation = Actual / Design; Cushion = 100% - Utilisation.
- Strategies: leading (ahead), following (after), tracking (small steps).
- N = Σ D x p / T (round up).
- BEP: Q = FC / (R - v); Profit = Q(R - v) - FC.
- Economies of scale below the optimal level; diseconomies above it.
- A bottleneck caps system output; constraints are managed in five repeating steps.

### 2.20 Practice Q&A: Capacity planning

**Q1. Why is capacity planning called strategic? Give three reasons.**

*A.* It commits large financial resources for the long term, is hard to reverse, and shapes future operating costs and competitiveness. It also determines whether the firm can meet future demand and must be planned well in advance.

**Q2. Distinguish between design capacity and effective capacity. Why can actual output never exceed effective capacity?**

*A.* Design capacity is the maximum output the facility is designed for. Effective capacity is design capacity minus allowances (maintenance, personal time, changeovers). Actual output is what is achieved in practice, and since those allowances are unavoidable, actual output is capped at effective capacity.

**Q3. A plant has design capacity 120 units/day, effective capacity 100 units/day and actual output 85 units/day. Compute efficiency, utilisation and capacity cushion.**

*A.* Efficiency = 85 / 100 = **85%**. Utilisation = 85 / 120 = **70.83%**. Capacity cushion = 100% - 70.83% = **29.17%**.

**Q4. Compare leading, following and tracking capacity strategies.**

*A.* Leading adds capacity before demand rises (avoids lost sales, risks idle capacity). Following adds capacity only after demand exceeds capacity (high utilisation, risks lost customers). Tracking adds capacity in small increments to keep pace with demand (a balance of the two, but needs flexibility).

**Q5. Why would a fashion retailer keep a larger capacity cushion than a bottled-water plant?**

*A.* Fashion demand is highly uncertain, so extra capacity absorbs surprises. Bottled water is a standard product with stable demand, so a small cushion and high utilisation are affordable.

**Q6. A shop makes products A, B and C. Annual demand is 20,000, 12,000 and 5,000 units; processing times are 0.10, 0.20 and 0.30 hours per unit. Each machine is available 2,000 hours a year. How many machines are required?**

*A.* Total hours = 2,000 + 2,400 + 1,500 = 5,900. N = 5,900 / 2,000 = 2.95, round up to **3 machines**.

**Q7. Four operations each supply 10 units/hr to a final operation that can process 30 units/hr. What is the system output and which operation is the bottleneck? What happens if you double the capacity of operation 1?**

*A.* Total input is 40/hr but the final operation handles only 30/hr, so system output is **30 units/hr** and the final operation is the bottleneck. Doubling operation 1 changes nothing for total output, because the bottleneck still limits flow.

**Q8. Explain economies and diseconomies of scale and give reasons for each.**

*A.* Economies of scale: average unit cost falls as output rises toward the optimal level because fixed costs are spread over more units, construction cost grows slower than size, and processing is standardised. Diseconomies of scale: beyond the optimal level, unit cost rises because of higher distribution costs and congestion, greater complexity, inflexibility and bureaucracy.

**Q9. Fixed costs are 60,000 per year, variable cost is 20 per unit and selling price is 50. Find the break-even quantity, the profit at 3,000 units, and the volume needed for a profit of 45,000.**

*A.* Contribution per unit = 30. Break-even = 60,000 / 30 = **2,000 units**. Profit at 3,000 = 3,000 x 30 - 60,000 = **30,000**. Volume for 45,000 profit = 105,000 / 30 = **3,500 units**.

**Q10. Machine A has fixed cost 100,000 and variable cost 12 per unit; Machine B has fixed cost 40,000 and variable cost 20 per unit. At what volume are they equally costly, and which is better above that volume?**

*A.* 100,000 + 12Q = 40,000 + 20Q gives 60,000 = 8Q, so **Q = 7,500 units**. Above 7,500 units Machine A is cheaper (lower variable cost); below it Machine B is cheaper.

**Q11. State the assumptions of cost-volume analysis. Which one is violated when capacity comes in step costs?**

*A.* One product; everything produced is sold; constant variable cost per unit; fixed costs unchanged with volume (or step changes only); constant revenue per unit; revenue per unit above variable cost per unit. Step costs break the assumption of constant fixed cost, which is why multiple break-even points can arise.

**Q12. An investment costs 10,000 today and returns 6,000 at the end of each of the next two years. At a 10% discount rate, is it worthwhile?**

*A.* PV = 6,000 / 1.10 + 6,000 / 1.21 = 5,454.55 + 4,958.68 = 10,413.22. NPV = 10,413.22 - 10,000 = **+413.22**, so it is (marginally) worthwhile financially.

**Q13. List the steps in resolving a constraint.**

*A.* Identify the most pressing constraint; change the operation to get maximum benefit given it; make sure other parts of the process support it; explore ways to overcome it; repeat until constraints are at acceptable levels.

**Q14. Services cannot be stored. How does this complicate capacity planning, and what demand management tactics help?**

*A.* Unused service capacity is lost forever, so capacity must match demand at the moment it occurs, and demand is volatile. Pricing, promotions and discounts that shift demand from peak to off-peak periods help balance supply and demand.
