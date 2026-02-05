# Components Reference

Production-ready markup and CSS for common crypto UI components. All components use the CSS custom property system from SKILL.md. Adapt markup to React JSX or framework syntax as needed.

## Wallet Connect Button

```html
<button class="wallet-btn" aria-label="Connect wallet">
  <span class="wallet-btn__icon">
    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
      <rect x="2" y="5" width="20" height="14" rx="2"/><path d="M16 12h.01"/>
    </svg>
  </span>
  <span class="wallet-btn__label">Connect Wallet</span>
</button>
```

```css
.wallet-btn {
  display: inline-flex;
  align-items: center;
  gap: var(--space-sm);
  padding: var(--space-sm) var(--space-lg);
  background: var(--accent-primary);
  color: var(--surface-base);
  border: none;
  border-radius: var(--radius-full);
  font-family: inherit;
  font-size: var(--font-size-sm);
  font-weight: 600;
  cursor: pointer;
  transition: all var(--transition-fast);
  position: relative;
  overflow: hidden;
}
.wallet-btn::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, transparent 40%, rgba(255,255,255,0.2) 50%, transparent 60%);
  transform: translateX(-100%);
  transition: transform 0.6s ease;
}
.wallet-btn:hover::before {
  transform: translateX(100%);
}
.wallet-btn:hover {
  box-shadow: var(--shadow-glow);
  transform: translateY(-1px);
}
.wallet-btn:active {
  transform: translateY(0) scale(0.98);
}
.wallet-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
  box-shadow: none;
}

/* Connected state */
.wallet-btn--connected {
  background: var(--surface-raised);
  color: var(--text-primary);
  border: 1px solid var(--border-interactive);
}
.wallet-btn--connected .wallet-btn__dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--color-success);
  animation: pulseGlow 2s ease-in-out infinite;
}
```

## Token Balance Display

```html
<div class="token-balance">
  <div class="token-balance__header">
    <img class="token-balance__icon" src="token-icon.svg" alt="ETH" width="32" height="32" />
    <div class="token-balance__info">
      <span class="token-balance__name">Ethereum</span>
      <span class="token-balance__symbol">ETH</span>
    </div>
  </div>
  <div class="token-balance__values">
    <span class="token-balance__amount">12.4582</span>
    <span class="token-balance__fiat">$31,284.20</span>
  </div>
  <span class="token-balance__change token-balance__change--positive">+3.42%</span>
</div>
```

```css
.token-balance {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--space-md) var(--space-lg);
  background: var(--surface-raised);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-lg);
  transition: all var(--transition-fast);
}
.token-balance:hover {
  border-color: var(--border-interactive);
  background: var(--surface-overlay);
}
.token-balance__header {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
}
.token-balance__icon {
  border-radius: var(--radius-full);
}
.token-balance__name {
  font-size: var(--font-size-base);
  font-weight: 500;
  color: var(--text-primary);
  display: block;
}
.token-balance__symbol {
  font-size: var(--font-size-sm);
  color: var(--text-muted);
}
.token-balance__values {
  text-align: right;
}
.token-balance__amount {
  font-size: var(--font-size-md);
  font-weight: 600;
  color: var(--text-primary);
  font-variant-numeric: tabular-nums;
  display: block;
}
.token-balance__fiat {
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  font-variant-numeric: tabular-nums;
}
.token-balance__change {
  font-size: var(--font-size-sm);
  font-weight: 500;
  padding: var(--space-xs) var(--space-sm);
  border-radius: var(--radius-sm);
}
.token-balance__change--positive {
  color: var(--color-success);
  background: rgba(0, 255, 136, 0.1);
}
.token-balance__change--negative {
  color: var(--color-error);
  background: rgba(255, 51, 85, 0.1);
}
```

## Transaction Table

```html
<div class="tx-table-wrapper">
  <table class="tx-table">
    <thead>
      <tr>
        <th>Type</th>
        <th>Hash</th>
        <th>Amount</th>
        <th>Status</th>
        <th>Time</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><span class="tx-type tx-type--send">Send</span></td>
        <td class="tx-hash" title="0xabc...def">
          <span>0xabc...def</span>
          <button class="copy-btn" aria-label="Copy hash">Copy</button>
        </td>
        <td class="tx-amount tx-amount--negative">-2.5 ETH</td>
        <td><span class="tx-status tx-status--confirmed">Confirmed</span></td>
        <td class="tx-time">2 min ago</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
.tx-table-wrapper {
  overflow-x: auto;
  border-radius: var(--radius-lg);
  border: 1px solid var(--border-subtle);
}
.tx-table {
  width: 100%;
  border-collapse: collapse;
  font-size: var(--font-size-sm);
}
.tx-table th {
  padding: var(--space-sm) var(--space-md);
  text-align: left;
  font-weight: 500;
  color: var(--text-muted);
  background: var(--surface-overlay);
  border-bottom: 1px solid var(--border-subtle);
  white-space: nowrap;
}
.tx-table td {
  padding: var(--space-sm) var(--space-md);
  border-bottom: 1px solid var(--border-subtle);
  color: var(--text-secondary);
  vertical-align: middle;
}
.tx-table tbody tr {
  transition: background var(--transition-fast);
}
.tx-table tbody tr:hover {
  background: var(--surface-interactive);
}
.tx-type {
  padding: 2px var(--space-sm);
  border-radius: var(--radius-sm);
  font-size: var(--font-size-xs);
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.tx-type--send { color: var(--color-error); background: rgba(255, 51, 85, 0.1); }
.tx-type--receive { color: var(--color-success); background: rgba(0, 255, 136, 0.1); }
.tx-type--swap { color: var(--color-info); background: rgba(0, 136, 255, 0.1); }
.tx-hash {
  font-family: var(--font-mono, monospace);
  display: flex;
  align-items: center;
  gap: var(--space-xs);
}
.tx-amount { font-variant-numeric: tabular-nums; font-weight: 500; }
.tx-amount--negative { color: var(--color-error); }
.tx-amount--positive { color: var(--color-success); }
.tx-status {
  padding: 2px var(--space-sm);
  border-radius: var(--radius-full);
  font-size: var(--font-size-xs);
  font-weight: 500;
}
.tx-status--confirmed { color: var(--color-success); background: rgba(0, 255, 136, 0.1); }
.tx-status--pending { color: var(--color-warning); background: rgba(255, 170, 0, 0.1); }
.tx-status--failed { color: var(--color-error); background: rgba(255, 51, 85, 0.1); }

/* Mobile: card-based layout */
@media (max-width: 767px) {
  .tx-table thead { display: none; }
  .tx-table tbody tr {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--space-xs);
    padding: var(--space-md);
    border-bottom: 1px solid var(--border-subtle);
  }
  .tx-table td {
    padding: 0;
    border: none;
  }
  .tx-table td::before {
    content: attr(data-label);
    display: block;
    font-size: var(--font-size-xs);
    color: var(--text-muted);
    margin-bottom: 2px;
  }
}
```

## Airdrop Claim Card

```html
<div class="claim-card">
  <div class="claim-card__header">
    <h3 class="claim-card__title">Token Airdrop</h3>
    <span class="claim-card__badge">Eligible</span>
  </div>
  <div class="claim-card__amount">
    <span class="claim-card__value">10,000</span>
    <span class="claim-card__token">TOKEN</span>
  </div>
  <div class="claim-card__details">
    <div class="claim-card__row">
      <span class="claim-card__label">Estimated Value</span>
      <span class="claim-card__data">$4,200.00</span>
    </div>
    <div class="claim-card__row">
      <span class="claim-card__label">Claim Deadline</span>
      <span class="claim-card__data">14d 6h 32m</span>
    </div>
  </div>
  <button class="claim-card__btn">Claim Tokens</button>
</div>
```

```css
.claim-card {
  background: var(--surface-raised);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-xl);
  padding: var(--space-xl);
  position: relative;
  overflow: hidden;
}
.claim-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
}
.claim-card__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: var(--space-lg);
}
.claim-card__title {
  font-size: var(--font-size-md);
  font-weight: 600;
  color: var(--text-primary);
  margin: 0;
}
.claim-card__badge {
  padding: var(--space-xs) var(--space-sm);
  background: rgba(0, 255, 136, 0.1);
  color: var(--color-success);
  border-radius: var(--radius-full);
  font-size: var(--font-size-xs);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.claim-card__amount {
  text-align: center;
  padding: var(--space-xl) 0;
}
.claim-card__value {
  font-size: var(--font-size-3xl);
  font-weight: 700;
  color: var(--text-primary);
  font-variant-numeric: tabular-nums;
  display: block;
  line-height: 1.1;
}
.claim-card__token {
  font-size: var(--font-size-md);
  color: var(--text-accent);
  font-weight: 500;
}
.claim-card__details {
  border-top: 1px solid var(--border-subtle);
  padding-top: var(--space-md);
  margin-bottom: var(--space-lg);
}
.claim-card__row {
  display: flex;
  justify-content: space-between;
  padding: var(--space-xs) 0;
}
.claim-card__label { color: var(--text-muted); font-size: var(--font-size-sm); }
.claim-card__data { color: var(--text-primary); font-size: var(--font-size-sm); font-weight: 500; }
.claim-card__btn {
  width: 100%;
  padding: var(--space-md);
  background: var(--accent-primary);
  color: var(--surface-base);
  border: none;
  border-radius: var(--radius-lg);
  font-family: inherit;
  font-size: var(--font-size-base);
  font-weight: 600;
  cursor: pointer;
  transition: all var(--transition-fast);
  position: relative;
  overflow: hidden;
}
.claim-card__btn:hover {
  box-shadow: var(--shadow-glow);
  transform: translateY(-1px);
}
.claim-card__btn:active {
  transform: translateY(0) scale(0.99);
}
```

## Countdown Timer

```html
<div class="countdown" aria-label="Time remaining">
  <div class="countdown__segment">
    <span class="countdown__value" data-countdown="days">14</span>
    <span class="countdown__label">Days</span>
  </div>
  <span class="countdown__separator">:</span>
  <div class="countdown__segment">
    <span class="countdown__value" data-countdown="hours">06</span>
    <span class="countdown__label">Hours</span>
  </div>
  <span class="countdown__separator">:</span>
  <div class="countdown__segment">
    <span class="countdown__value" data-countdown="minutes">32</span>
    <span class="countdown__label">Min</span>
  </div>
  <span class="countdown__separator">:</span>
  <div class="countdown__segment">
    <span class="countdown__value" data-countdown="seconds">08</span>
    <span class="countdown__label">Sec</span>
  </div>
</div>
```

```css
.countdown {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
}
.countdown__segment {
  text-align: center;
  min-width: 56px;
  padding: var(--space-sm) var(--space-md);
  background: var(--surface-overlay);
  border-radius: var(--radius-md);
  border: 1px solid var(--border-subtle);
}
.countdown__value {
  display: block;
  font-size: var(--font-size-xl);
  font-weight: 700;
  color: var(--text-primary);
  font-variant-numeric: tabular-nums;
  line-height: 1.2;
}
.countdown__label {
  font-size: var(--font-size-xs);
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.countdown__separator {
  font-size: var(--font-size-xl);
  color: var(--text-muted);
  font-weight: 300;
}
```

## Address Display with Copy

```html
<div class="address-display">
  <span class="address-display__text" title="0x742d35Cc6634C0532925a3b844Bc9e7595f2bD18">
    0x742d...f2bD18
  </span>
  <button class="address-display__copy" aria-label="Copy address">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
      <rect x="9" y="9" width="13" height="13" rx="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/>
    </svg>
  </button>
</div>
```

```css
.address-display {
  display: inline-flex;
  align-items: center;
  gap: var(--space-xs);
  padding: var(--space-xs) var(--space-sm);
  background: var(--surface-overlay);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  font-family: var(--font-mono, monospace);
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
}
.address-display__copy {
  display: flex;
  align-items: center;
  background: none;
  border: none;
  color: var(--text-muted);
  cursor: pointer;
  padding: 2px;
  border-radius: var(--radius-sm);
  transition: color var(--transition-fast);
}
.address-display__copy:hover {
  color: var(--accent-primary);
}
```

## Network Status Indicator

```html
<div class="network-status">
  <span class="network-status__dot network-status__dot--active"></span>
  <span class="network-status__name">Ethereum Mainnet</span>
  <span class="network-status__block">Block: 19,234,567</span>
</div>
```

```css
.network-status {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  padding: var(--space-xs) var(--space-md);
  background: var(--surface-raised);
  border-radius: var(--radius-full);
  font-size: var(--font-size-xs);
  border: 1px solid var(--border-subtle);
}
.network-status__dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  flex-shrink: 0;
}
.network-status__dot--active {
  background: var(--color-success);
  box-shadow: 0 0 6px var(--color-success);
}
.network-status__dot--degraded {
  background: var(--color-warning);
  box-shadow: 0 0 6px var(--color-warning);
}
.network-status__dot--offline {
  background: var(--color-error);
}
.network-status__name {
  color: var(--text-primary);
  font-weight: 500;
}
.network-status__block {
  color: var(--text-muted);
  font-variant-numeric: tabular-nums;
}
```

## Staking Card

```html
<div class="staking-card">
  <div class="staking-card__header">
    <h3 class="staking-card__title">Stake ETH</h3>
    <span class="staking-card__apy">APY 4.2%</span>
  </div>
  <div class="staking-card__input-group">
    <label class="staking-card__label" for="stake-amount">Amount</label>
    <div class="staking-card__input-wrapper">
      <input class="staking-card__input" id="stake-amount" type="text" placeholder="0.00" inputmode="decimal" />
      <button class="staking-card__max-btn">MAX</button>
    </div>
    <span class="staking-card__balance">Balance: 12.458 ETH</span>
  </div>
  <button class="staking-card__submit">Stake</button>
</div>
```

```css
.staking-card {
  background: var(--surface-raised);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-xl);
  padding: var(--space-xl);
}
.staking-card__header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: var(--space-lg);
}
.staking-card__title {
  font-size: var(--font-size-lg);
  font-weight: 600;
  color: var(--text-primary);
  margin: 0;
}
.staking-card__apy {
  color: var(--color-success);
  font-weight: 600;
  font-size: var(--font-size-sm);
}
.staking-card__label {
  display: block;
  color: var(--text-muted);
  font-size: var(--font-size-sm);
  margin-bottom: var(--space-xs);
}
.staking-card__input-wrapper {
  display: flex;
  align-items: center;
  background: var(--surface-base);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  overflow: hidden;
  transition: border-color var(--transition-fast);
}
.staking-card__input-wrapper:focus-within {
  border-color: var(--accent-primary);
}
.staking-card__input {
  flex: 1;
  background: transparent;
  border: none;
  padding: var(--space-md);
  color: var(--text-primary);
  font-family: inherit;
  font-size: var(--font-size-lg);
  font-variant-numeric: tabular-nums;
  outline: none;
}
.staking-card__input::placeholder {
  color: var(--text-muted);
}
.staking-card__max-btn {
  padding: var(--space-xs) var(--space-sm);
  margin-right: var(--space-sm);
  background: var(--surface-interactive);
  color: var(--accent-primary);
  border: none;
  border-radius: var(--radius-sm);
  font-family: inherit;
  font-size: var(--font-size-xs);
  font-weight: 600;
  cursor: pointer;
  transition: background var(--transition-fast);
}
.staking-card__max-btn:hover {
  background: var(--accent-glow);
}
.staking-card__balance {
  display: block;
  margin-top: var(--space-xs);
  font-size: var(--font-size-xs);
  color: var(--text-muted);
}
.staking-card__submit {
  width: 100%;
  margin-top: var(--space-lg);
  padding: var(--space-md);
  background: var(--accent-primary);
  color: var(--surface-base);
  border: none;
  border-radius: var(--radius-lg);
  font-family: inherit;
  font-size: var(--font-size-base);
  font-weight: 600;
  cursor: pointer;
  transition: all var(--transition-fast);
}
.staking-card__submit:hover {
  box-shadow: var(--shadow-glow);
  transform: translateY(-1px);
}
.staking-card__submit:active {
  transform: translateY(0) scale(0.99);
}
.staking-card__submit:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
}
```
