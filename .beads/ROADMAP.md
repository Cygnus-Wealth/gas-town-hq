# Cygnus Wealth Roadmap

## Wave 1a — Green Tests (unit)
- [x] `da-ct3` Green tests: DataModels
- [x] `ev-2y9` Green tests: EvmIntegration
- [x] `wa-0by` Green tests: WalletIntegrationSystem
- [x] `as-7cb` Green tests: AssetValuator
- [x] `po-u5q` Green tests: PortfolioAggregation
- [x] `so-bmk` Green tests: SolIntegration
- [x] `ro-y7j` Green tests: RobinhoodIntegration
- [x] `cy-k7zd` Green tests: CygnusWealthApp
- [x] `cy-5wx8` Fix missing wallet icons (Phantom, Slush)

## Wave 1b — Testnet Support (convoy hq-cv-eyefa)
- [x] `da-2dd` NetworkEnvironment type (DataModels)
- [x] `wa-vrx` Chain presets per environment (WalletIntegrationSystem)
- [x] `cy-cv2` Environment detection + UI indicator (CygnusWealthApp)
- [x] `so-8ii` Environment-aware Solana facade (SolIntegration)
- [x] `po-yu1` Environment validation + cache isolation (PortfolioAggregation)
- [x] `as-1lp` TestPriceProvider + env-based selection (AssetValuator)
- [x] `ev-djf` Environment-aware ChainRegistry (EvmIntegration)

## Wave 1c — Infrastructure
- [x] `hq-rgo3h` RPC node strategy (EnterpriseArch)

## Wave 1d — E2E Testing Strategy (after 1b + 1c)
- [x] `hq-p9nwf` Enterprise E2E policy: define per bounded context (EnterpriseArch)
- [x] `ev-qukl` EvmIntegration: fix E2E, align with strategy
- [x] `wa-6sj` WalletIntegrationSystem: new E2E suite
- [x] `ro-41g` RobinhoodIntegration: Vitest upgrade + 14 E2E tests
- [x] `as-owr3` AssetValuator: Jest→Vitest migration + 15 E2E tests
- [x] `po-pvu` PortfolioAggregation: orchestration E2E (28+ tests)
- [x] `so-0j1` SolIntegration: review/document E2E (21 tests)
- [x] `cy-o1md` CygnusWealthApp: Playwright E2E expanded

## Wave 2 — Core Features (after Wave 1)
- [ ] `ev-9lg` ERC20 token balances (EvmIntegration) — depends on hq-rgo3h
- [ ] `da-syn` DeFi position types (DataModels)
- [ ] `wa-7xe` Crypto.com onchain wallet (WalletIntegrationSystem)
- [ ] `wa-271` Trust Wallet support (WalletIntegrationSystem)
- [ ] `po-59f` Multi-account aggregation (PortfolioAggregation)

## Wave 3 — DeFi Integration (after da-syn)
- [ ] `ev-82k` DeFi protocol integration: Beefy, Aave, etc. (EvmIntegration)

## Wave 4 — DeFi Aggregation (after ev-82k)
- [ ] `po-e31` DeFi position aggregation (PortfolioAggregation)

## Wave 5 — DeFi UI (after po-e31)
- [ ] `cy-kzf5` DeFi positions UI in dashboard (CygnusWealthApp)

## Wave 6 — CEX Integrations (after Wave 5)
- [ ] `da-8l3` CEX account types (DataModels)
- [ ] `ro-7ft` Robinhood integration (RobinhoodIntegration)
- [ ] `hq-onegb` Coinbase integration (new rig)
- [ ] `hq-su5pt` Kraken integration (new rig)
- [ ] `cy-ifbg` CEX holdings UI (CygnusWealthApp)

## Last — Testnet Fixtures (after features land)
- [ ] `cy-4xiu` Testnet demo fixtures: pre-populated data for all features

## Dependency Chains

```
Wave 1a: Green tests x8 + icons — DONE
Wave 1b: Testnet support x7 — DONE
Wave 1c: RPC strategy — DONE
Wave 1d: E2E enterprise policy + per-rig trickle down — DONE
Wave 2:  ERC20 ← 1c, DeFi types, wallets, multi-acct — all parallel
Wave 3:  DeFi integration ← da-syn
Wave 4:  DeFi aggregation ← ev-82k
Wave 5:  DeFi UI ← po-e31
Wave 6:  CEX types → CEX integrations → CEX UI
Last:    Testnet fixtures ← everything
```
