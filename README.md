# Camunda BPMN + DMN Exercises

## Exercise 1 — Loan Application Risk Routing
Files:
- `exercise-1-loan-risk/loan-risk-routing.bpmn`
- `exercise-1-loan-risk/evaluate-loan-risk.dmn`

Business Rule Task:
- Decision: `evaluate-loan-risk`
- Map Decision Result: `Single Result`
- Result variable: `loanRisk`

Gateway conditions use FEEL:
- `= loanRisk.riskTier = "LOW"`
- `= loanRisk.riskTier = "MEDIUM" or loanRisk.requiresManualReview = true`
- `= loanRisk.riskTier = "HIGH" and loanRisk.requiresManualReview = false`

## Exercise 2 — Multi-Item Order Discount & Fulfillment
Files:
- `exercise-2-order-discount/order-discount-fulfillment.bpmn`
- `exercise-2-order-discount/calculate-discounts.dmn`

DMN:
- Hit Policy: Collect
- Aggregation: Sum (`C+`)
- Output: `discountPercent`

Business Rule Task:
- Map Decision Result: `Single Entry`
- Result variable: `totalDiscount`

Sample:
- `customerTier = "PREMIUM"`
- `cartValue = 600`
- `promoCode = "FESTIVE10"`

Matching discounts = 10 + 5 + 10 + 0 = **25%**.
Final amount = `600 * (1 - 25/100) = 450`.
Because `450 < 1000`, the order proceeds directly to **Send Order to Warehouse**.

## Open in Camunda Modeler
Open each `.bpmn` and `.dmn` file in Camunda Modeler. The BPMN files include diagram interchange coordinates so the process is laid out automatically.
