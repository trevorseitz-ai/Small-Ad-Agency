# Research: The Replit Survival Manual

## 1. Research Status
- Status: Initial research pass complete. Requires verification before drafting.
- Date checked: 2026-06-07
- Research scope: Official Replit documentation regarding Workspaces, Agents, Billing, and Deployments.
- Remaining blockers: Verification of exact pricing rates, credit costs, and specific rollover behaviors for Starter and Core plans.

## 2. Official Sources Reviewed
- Source title: Replit Pricing Page
  - URL: https://replit.com/pricing
  - Source type: Official Pricing Documentation
  - Date checked: 2026-06-07
  - Notes: Mentions presence of credit allowances in subscription tiers, but lacks detailed hourly or per-token consumption rates for workspace cycles.
- Source title: Replit Account Usage and Limits Docs
  - URL: https://docs.replit.com/power-features/account-usage
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Notes: Explains checking resource consumption and setting spending caps.
- Source title: Replit Agent Getting Started
  - URL: https://docs.replit.com/replit-agent/getting-started
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Notes: Details Agent functionality and configuration options like Economy/Power modes.
- Source title: Replit Deployments Overview
  - URL: https://docs.replit.com/deployments/about-deployments
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Notes: Explains Static, Autoscale, Reserved VM, and Scheduled deployments.

## 3. Verified Platform Facts
- Finding: Replit uses a unified credit pool model where subscription plans receive a monthly credit allowance that covers Agent usage, database operations, storage, and hosting deployments.
  - Source URL: https://docs.replit.com/power-features/account-usage
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: High
  - Notes: Explicitly documented as a unified pool.
- Finding: Replit provides Economy, Power, and Turbo modes for the Replit Agent to manage model size and performance tiers.
  - Source URL: https://docs.replit.com/replit-agent/getting-started
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: High
  - Notes: Toggles are available in the Agent interface settings.

## 4. Pricing and Credit Findings
- Finding: Paid plans (Core and Pro) include recurring monthly credit allowances. If these credits are exhausted, usage continues on a pay-as-you-go basis.
  - Source URL: https://replit.com/pricing
  - Source type: Official Pricing Documentation
  - Date checked: 2026-06-07
  - Confidence: High
  - Notes: Basic tier structure is verified, but exact credit rates per CPU-hour or token require live checkout verification.
- Finding: Credit rollover rules and allowances.
  - Source URL: https://replit.com/pricing
  - Source type: Official Pricing Documentation
  - Date checked: 2026-06-07
  - Confidence: Low
  - Notes: Needs verification before drafting.
- Finding: Daily credit allocation and expiration policies.
  - Source URL: https://replit.com/pricing
  - Source type: Official Pricing Documentation
  - Date checked: 2026-06-07
  - Confidence: Low
  - Notes: Needs verification before drafting.

## 5. Development and Workspace Findings
- Finding: Workspace storage capacity limits and performance constraints per tier.
  - Source URL: https://docs.replit.com/power-features/account-usage
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: Low
  - Notes: Needs verification before drafting.
- Finding: Workspace process interruptions during resource capacity limits.
  - Source URL: https://docs.replit.com/power-features/account-usage
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: Low
  - Notes: Needs verification before drafting.
- Finding: Code compilation loop errors and runaway agent cycles.
  - Source URL: https://docs.replit.com/replit-agent/getting-started
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: Low
  - Notes: Needs verification before drafting.

## 6. Deployment and Publishing Findings
- Finding: Replit supports multiple deployment options, including Static, Autoscale, Reserved VM, and Scheduled deployments.
  - Source URL: https://docs.replit.com/deployments/about-deployments
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: High
  - Notes: The categories are verified, but pricing rates are variable.
- Finding: Static Deployments host client-side assets (HTML/CSS/JS) and bypass persistent compute charges.
  - Source URL: https://docs.replit.com/deployments/about-deployments
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: High
  - Notes: Client-side static limitation is officially verified.
- Finding: Autoscale Deployments dynamically scale down when idle, charging a base fee and compute resource fees when serving requests.
  - Source URL: https://docs.replit.com/deployments/about-deployments
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: High
  - Notes: Base fee rate and compute scale-to-zero function are verified, but exact monthly pricing needs verification before drafting.
- Finding: Reserved VM Deployments run continuously on dedicated CPU/RAM configurations with flat-rate monthly billing.
  - Source URL: https://docs.replit.com/deployments/about-deployments
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: High
  - Notes: Dedicated VM resource allocation is verified, but exact base fee needs verification before drafting.

## 7. Spend Management Findings
- Finding: Hard budgets and usage caps can be set in user settings to restrict compute overages.
  - Source URL: https://docs.replit.com/power-features/account-usage
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: High
  - Notes: Usage dashboard tools and spend limits are verified as active account features.
- Finding: Plan Mode's impact on token and credit consumption rates.
  - Source URL: https://docs.replit.com/replit-agent/getting-started
  - Source type: Official Product Documentation
  - Date checked: 2026-06-07
  - Confidence: Low
  - Notes: Needs verification before drafting.

## 8. Author Recommendations to Develop Later
*Note: The following are proposed guidelines and heuristics based on user experience, not official Replit platform constraints.*
- Engage with the Agent in Plan Mode first to discuss structure before running code edits. (Needs verification before drafting).
- Set spending caps inside the Replit Account settings page immediately upon project setup to limit runaway costs.
- Supply micro-prompts rather than large system-wide requests to prevent code loops. (Needs verification before drafting).
- Use Economy Mode for documentation and basic CSS styling work; preserve Power/Turbo modes for algorithmic logic and complex debugging.
- Bypass Replit deployment costs for pure static sites by compiling assets in the workspace and deploying to external static hosts. (Needs verification before drafting).
- Choose Autoscale configurations over Reserved VMs for low-traffic backend microservices. (Needs verification before drafting).

## 9. Needs Verification Before Drafting
- The exact pricing and credit ratios for the Starter, Core, and Pro subscription tiers.
- Rollover details and credit lifetime limits per plan.
- The direct cost impact of Plan Mode on credit consumption.
- Specific resource limits (storage and compute capacity) per workspace tier.
- Detailed behaviors of Agent compile loops and resource consumption.

## 10. Citation Map
- Topic: Subscription Plan Credit Allocations -> https://replit.com/pricing
- Topic: Spending Caps and Budget Controls -> https://docs.replit.com/power-features/account-usage
- Topic: Agent Mode Efficiencies (Economy/Power/Turbo) -> https://docs.replit.com/replit-agent/getting-started
- Topic: Deployment Hosting Types and Compute Costs -> https://docs.replit.com/deployments/about-deployments
