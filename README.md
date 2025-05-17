<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1" />
<title>$OKAPI TOKEN Farming Bot</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    font-family: 'Inter', sans-serif;
    background: #05070f;
    color: #d0f5e8;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  header {
    background: #081425;
    padding: 20px 40px;
    text-align: center;
    font-weight: 700;
    font-size: 1.8rem;
    color: #39ffca;
    letter-spacing: 2.2px;
    user-select: none;
    box-shadow: 0 2px 8px #0a645eaa;
  }
  nav {
    display: flex;
    background: #0a203b;
    justify-content: space-around;
    border-bottom: 3px solid #22ffcc;
    box-shadow: inset 0 -4px 12px #077f6899;
  }
  nav button {
    flex-grow: 1;
    background: transparent;
    border: none;
    padding: 16px 12px;
    cursor: pointer;
    font-size: 1.05rem;
    color: #6fffdccc;
    transition: color 0.25s ease;
    font-weight: 700;
    letter-spacing: 0.9px;
    outline-offset: 3px;
    outline-color: transparent;
    outline-style: solid;
    user-select: none;
  }
  nav button:hover,
  nav button:focus,
  nav button.active {
    color: #00ffdb;
    border-bottom: 3px solid #00ffdb;
    outline-color: #00ffdb;
  }
  main {
    max-width: 900px;
    margin: 30px auto 60px auto;
    padding: 0 20px 40px;
    background: #0a1835;
    border-radius: 16px;
    box-shadow:
      0 1px 5px #00776577,
      0 4px 12px #009988aa;
    min-height: 520px;
  }
  h2 {
    color: #00edcc;
    margin-bottom: 20px;
    letter-spacing: 0.5px;
    font-weight: 800;
    text-shadow: 0 0 6px #00ffccbb;
  }
  button.primary {
    background: linear-gradient(135deg, #00dab6, #00ffc9);
    border: none;
    outline: none;
    padding: 14px 26px;
    color: #00382e;
    font-weight: 700;
    font-size: 1.12rem;
    border-radius: 12px;
    cursor: pointer;
    transition: background 0.3s ease, color 0.3s ease;
    letter-spacing: 1.1px;
    user-select: none;
  }
  button.primary:hover:enabled,
  button.primary:focus-visible:enabled {
    background: linear-gradient(135deg, #00ffc9, #00dab6);
    color: #001b11;
    box-shadow: 0 0 10px #00f2c3dd;
  }
  button.primary:disabled {
    background: #044d3a90;
    cursor: not-allowed;
    color: #00402eaa;
  }
  input[type="number"], input[type="text"] {
    padding: 14px 18px;
    font-size: 1.1rem;
    border-radius: 14px;
    border: none;
    outline: none;
    width: 100%;
    max-width: 220px;
    background: #0b203b;
    color: #a8fff0;
    margin-right: 20px;
    font-weight: 600;
    box-shadow: inset 0 0 8px #00ffccaa;
    transition: box-shadow 0.4s ease;
  }
  input[type="number"]:focus,
  input[type="text"]:focus {
    box-shadow: 0 0 15px #00ffd0cc;
  }
  label {
    color: #63ffdb;
    font-weight: 700;
    margin-right: 14px;
    min-width: 140px;
  }
  .field-row {
    display: flex;
    align-items: center;
    margin-bottom: 28px;
    flex-wrap: wrap;
    gap: 12px 14px;
  }
  .info-box {
    background: #121f3b;
    padding: 24px 30px;
    border-radius: 20px;
    color: #40fbd9cc;
    margin-bottom: 36px;
    line-height: 1.6;
    font-weight: 600;
    box-shadow:
      inset 0 0 12px #00ffd2cc;
  }
  .task-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  .task-list li {
    background: #0a344f;
    border: 1.8px solid #18e4baaa;
    border-radius: 18px;
    padding: 16px 24px;
    margin-bottom: 16px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #a0ffee;
    font-weight: 600;
    font-size: 1.05rem;
    user-select: none;
    box-shadow: 0 0 6px #00ffccee;
  }
  .task-list button {
    font-size: 1rem;
    padding: 10px 20px;
    background: #00ffc9cc;
    border: none;
    border-radius: 14px;
    font-weight: 800;
    cursor: pointer;
    color: #003628;
    letter-spacing: 0.9px;
    user-select: none;
    transition: background 0.3s ease;
  }
  .task-list button:disabled {
    background: #056653a8;
    cursor: not-allowed;
  }
  .task-list button:hover:enabled,
  .task-list button:focus-visible:enabled {
    background: #00f5b6;
    color: #00291f;
    box-shadow: 0 0 12px #00fdd190;
  }
  .referral-link {
    background: #0b203f;
    padding: 22px 26px;
    border-radius: 20px;
    color: #00ffce;
    word-break: break-all;
    user-select: all;
    margin-bottom: 26px;
    font-weight: 700;
    font-size: 1.1rem;
    box-shadow: inset 0 0 12px #00ffcadd;
  }
  .wallet-info {
    background: #0a3f2a;
    padding: 18px 22px;
    border-radius: 16px;
    font-weight: 700;
    color: #b6ffdf;
    letter-spacing: 1.0px;
    margin-bottom: 26px;
    box-shadow: 0 0 14px #00ffccbb;
    user-select: text;
  }
  .alert {
    background: #004644;
    border-radius: 14px;
    padding: 16px 18px;
    color: #a3ffdd;
    margin-bottom: 28px;
    font-size: 1.0rem;
    font-weight: 700;
    box-shadow: 0 0 15px #02ffccbb;
  }
  .boost-option {
    background: #08304a;
    border-radius: 20px;
    padding: 22px 28px;
    margin-bottom: 24px;
    border: 2px solid #066e6e;
    cursor: pointer;
    transition: border-color 0.4s ease, box-shadow 0.4s ease;
    display: flex;
    flex-direction: column;
    user-select: none;
  }
  .boost-option.selected {
    border-color: #00ffdf;
    box-shadow: 0 0 20px #00ffdfee;
  }
  .boost-option h3 {
    margin: 0 0 10px 0;
    color: #3cffd5;
    font-size: 1.35rem;
    font-weight: 800;
    text-shadow: 0 0 7px #00ffdda0;
  }
  .boost-option p {
    margin: 0;
    color: #7df5d4;
    font-weight: 600;
    font-size: 1.05rem;
    line-height: 1.3;
  }
  .copy-btn {
    background: #00b588;
    border: none;
    color: white;
    padding: 12px 18px;
    font-size: 1.05rem;
    border-radius: 14px;
    cursor: pointer;
    font-weight: 700;
    user-select: none;
    transition: background 0.3s ease;
  }
  .copy-btn:hover,
  .copy-btn:focus-visible {
    background: #00ffc3;
    color: #004a31;
    box-shadow: 0 0 12px #00ffd5aa;
  }
  footer {
    text-align: center;
    color: #005f57cc;
    font-size: 0.9rem;
    margin: 50px 0 32px;
    user-select: none;
    letter-spacing: 1.2px;
  }
  /* Farming additional controls */
  #farm-status {
    font-size: 1.2rem;
    font-weight: 700;
    margin-top: 20px;
    color: #00ffccdd;
    user-select: none;
    text-shadow: 0 0 6px #00ffccbb;
  }
  #farm-timer {
    font-weight: 900;
    font-size: 1.6rem;
    color: #7affff;
    margin-top: 8px;
    letter-spacing: 1.1px;
    user-select: text;
  }
  #farm-action-btn {
    margin-top: 28px;
    background: linear-gradient(135deg, #00a88e, #00ffcc);
    border: none;
    padding: 18px 38px;
    font-size: 1.3rem;
    font-weight: 900;
    border-radius: 16px;
    color: #001f14;
    cursor: pointer;
    letter-spacing: 1.4px;
    user-select: none;
    box-shadow: 0 0 12px #00ffccbb;
    transition: background 0.3s ease, box-shadow 0.3s ease;
  }
  #farm-action-btn:hover:enabled,
  #farm-action-btn:focus-visible:enabled {
    background: linear-gradient(135deg, #00ffc1, #00bca1);
    box-shadow: 0 0 20px #00ffccee;
    outline: none;
  }
  #farm-action-btn:disabled {
    background: #044d3a90;
    cursor: not-allowed;
    color: #003822aa;
    box-shadow: none;
  }
  #farm-level {
    margin-top: 16px;
    font-weight: 700;
    font-size: 1.1rem;
    color: #53ffee;
    text-shadow: 0 0 5px #11ffaaaa;
    user-select: none;
  }
  @media (max-width: 540px) {
    nav {
      flex-wrap: wrap;
    }
    nav button {
      flex: 1 0 48%;
      margin-bottom: 6px;
      font-size: 1.1rem;
      border-radius: 12px 12px 0 0;
      padding: 14px 12px;
    }
    nav button:last-child {
      margin-bottom: 10px;
    }
    h2 {
      font-size: 1.5rem;
    }
    main {
      margin: 24px 12px 60px;
      border-radius: 14px;
      padding: 12px 16px 30px;
      min-height: 520px;
    }
    .field-row {
      flex-direction: column;
      align-items: stretch;
      margin-bottom: 24px;
    }
    label {
      margin-bottom: 8px;
      min-width: 100%;
      text-align: left;
    }
    input[type="number"], input[type="text"] {
      max-width: 100%;
      margin-right: 0;
    }
    button.primary, .copy-btn, .task-list button, #farm-action-btn {
      width: 100%;
      font-size: 1.25rem;
      padding: 16px 0;
      border-radius: 14px;
      user-select: none;
    }
    .boost-option {
      padding: 18px 20px;
      margin-bottom: 20px;
      border-radius: 16px;
    }
    .boost-option h3 {
      font-size: 1.2rem;
    }
    .boost-option p {
      font-size: 1rem;
    }
    .task-list li {
      font-size: 1.05rem;
      padding: 14px 20px;
      border-radius: 14px;
    }
    .referral-link {
      font-size: 1.03rem;
      padding: 16px 18px;
      border-radius: 14px;
    }
    .wallet-info {
      font-size: 1.1rem;
      padding: 16px 22px;
      border-radius: 14px;
    }
    footer {
      font-size: 0.85rem;
      margin: 36px 0 24px;
    }
  }
</style>
</head>
<body>
<header>$OKAPI TOKEN Farming Bot</header>
<nav role="navigation" aria-label="Primary Navigation">
  <button class="active" data-page="farming">Farming</button>
  <button data-page="booster">Booster</button>
  <button data-page="invite">Invite</button>
  <button data-page="daily">Daily Task</button>
  <button data-page="wallet">Wallet Connect</button>
</nav>
<main>
  <!-- Farming Page -->
  <section id="farming" class="page" aria-label="Farming Page">
    <h2>Farm Your $OKAPI Tokens</h2>
    <div class="info-box" aria-live="polite" aria-atomic="true" id="general-info">
      Stake your $OKAPI tokens here and start earning rewards daily! Connect your wallet to begin.
    </div>
    <form id="stake-form" aria-label="Stake form">
      <div class="field-row">
        <label for="stake-amount">Amount to Stake:</label>
        <input type="number" id="stake-amount" min="0" step="0.0001" placeholder="0.0" aria-describedby="stake-info" required />
        <button class="primary" id="stake-btn" disabled type="submit" aria-disabled="true" aria-label="Stake $OKAPI Tokens">Stake</button>
      </div>
    </form>
    <div id="staked-info" class="info-box" aria-live="polite" style="display:none;">
      You have staked: <span id="staked-amount">0</span> $OKAPI Token(s)
    </div>

    <!-- Farm level display -->
    <div id="farm-level" aria-live="polite" aria-atomic="true" aria-label="Your farming level">
      Level: <span id="level-value">1</span>
    </div>

    <!-- Farming action controls -->
    <div id="farm-status" aria-live="polite" aria-atomic="true" style="margin-top:20px;"></div>
    <div id="farm-timer" aria-live="polite" aria-atomic="true" role="timer" style="user-select:text;"></div>

    <button id="farm-action-btn" disabled aria-disabled="true" aria-label="Start Farming or Collect Rewards">Tapping</button>
  </section>

  <!-- Booster Page -->
  <section id="booster" class="page" hidden aria-label="Booster Page">
    <h2>Farming Boosters</h2>
    <div class="info-box">
      Boost your farming rewards by activating one of the boosters below. Select a booster and press activate.
    </div>
    <div id="boosters-container" role="list" aria-label="List of boosters">
      <div class="boost-option" data-multiplier="1.1" tabindex="0" role="button" aria-pressed="false" aria-label="Booster 1.1x - Basic Booster" role="listitem">
        <h3>Basic Booster</h3>
        <p>Increase rewards by 10%. Cost: 50 $OKAPI</p>
      </div>
      <div class="boost-option" data-multiplier="1.3" tabindex="0" role="button" aria-pressed="false" aria-label="Booster 1.3x - Advanced Booster" role="listitem">
        <h3>Advanced Booster</h3>
        <p>Increase rewards by 30%. Cost: 120 $OKAPI</p>
      </div>
      <div class="boost-option" data-multiplier="1.5" tabindex="0" role="button" aria-pressed="false" aria-label="Booster 1.5x - Pro Booster" role="listitem">
        <h3>Pro Booster</h3>
        <p>Increase rewards by 50%. Cost: 200 $OKAPI</p>
      </div>
    </div>
    <button class="primary" id="activate-booster-btn" disabled aria-disabled="true" aria-label="Activate selected booster">Activate Booster</button>
    <div id="active-booster-info" class="info-box" aria-live="polite" style="display:none;">
      Active Booster: <span id="active-booster">None</span>
    </div>
  </section>

  <!-- Invite Page -->
  <section id="invite" class="page" hidden aria-label="Invite Page">
    <h2>Invite & Earn</h2>
    <div class="info-box">
      Share your referral link and earn bonuses when your friends join.
    </div>
    <div class="field-row" style="flex-wrap: wrap;">
      <input type="text" id="referral-link" readonly aria-label="Referral Link" />
      <button class="copy-btn" id="copy-referral-btn" aria-label="Copy referral link to clipboard" disabled>Copy</button>
    </div>
    <div class="info-box">
      Total Invites: <span id="total-invites">0</span><br />
      Earned Bonuses: <span id="earned-bonuses">0</span> $OKAPI
    </div>
  </section>

  <!-- Daily Task Page -->
  <section id="daily" class="page" hidden aria-label="Daily Task Page">
    <h2>Daily Tasks</h2>
    <ul class="task-list" id="task-list" aria-live="polite" aria-relevant="additions removals"></ul>
  </section>

  <!-- Wallet Connect Page -->
  <section id="wallet" class="page" hidden aria-label="Wallet Connect Page">
    <h2>Wallet Connect</h2>
    <button class="primary" id="connect-wallet-btn" aria-label="Connect or disconnect your wallet">Connect Wallet</button>
    <div id="wallet-info" class="wallet-info" style="display:none;" aria-live="polite"></div>
  </section>
</main>
<footer>
  &copy; 2025 $OKAPI TOKEN Farming Bot. All rights reserved.
</footer>

<!-- Libraries: ethers.js, walletconnect, web3modal -->
<script src="https://cdn.jsdelivr.net/npm/ethers/dist/ethers.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@walletconnect/web3-provider@1.7.8/dist/umd/index.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/web3modal@1.9.12/dist/index.js"></script>

<script>
(() => {
  'use strict';

  // Navigation tabs
  const navButtons = document.querySelectorAll('nav button');
  const pages = document.querySelectorAll('main .page');

  function showPage(pageId) {
    pages.forEach(p => p.hidden = p.id !== pageId);
    navButtons.forEach(btn => {
      const active = btn.dataset.page === pageId;
      btn.classList.toggle('active', active);
      btn.setAttribute('aria-current', active ? 'page' : 'false');
    });
  }

  navButtons.forEach(btn => btn.addEventListener('click', () => showPage(btn.dataset.page)));
  showPage('farming');

  // State variables
  let walletAddress = null;
  let isWalletConnected = false;

  let stakedAmount = 0;
  let activeBooster = null;  // {name:, multiplier:}
  let referralLink = '';
  let totalInvites = 0;
  let earnedBonuses = 0;
  let farmingLevel = 1;
  let farmingSessionsCompleted = 0;

  // Farming session state
  // {startTimestamp: number|null, collectedRewards: boolean}
  let farmingState = {
    startTimestamp: null,
    collectedRewards: false
  };

  // Constants
  const FARM_DURATION_MS = 3 * 60 * 60 * 1000; // 3 hours in milliseconds

  // DOM references
  const stakeInput = document.getElementById('stake-amount');
  const stakeBtn = document.getElementById('stake-btn');
  const stakedInfo = document.getElementById('staked-info');
  const stakedAmountSpan = document.getElementById('staked-amount');

  const boosters = document.querySelectorAll('.boost-option');
  const activateBoosterBtn = document.getElementById('activate-booster-btn');
  const activeBoosterInfo = document.getElementById('active-booster');
  const activeBoosterInfoBox = document.getElementById('active-booster-info');

  const referralLinkInput = document.getElementById('referral-link');
  const copyReferralBtn = document.getElementById('copy-referral-btn');
  const totalInvitesSpan = document.getElementById('total-invites');
  const earnedBonusesSpan = document.getElementById('earned-bonuses');

  const taskList = document.getElementById('task-list');

  const connectWalletBtn = document.getElementById('connect-wallet-btn');
  const walletInfo = document.getElementById('wallet-info');

  const farmStatusDiv = document.getElementById('farm-status');
  const farmTimerDiv = document.getElementById('farm-timer');
  const farmActionBtn = document.getElementById('farm-action-btn');
  const levelValueSpan = document.getElementById('level-value');
  const generalInfoBox = document.getElementById('general-info');

  // Initialize web3modal
  let web3Modal = null;
  let provider = null;
  let ethersProvider = null;

  async function initWeb3Modal() {
    web3Modal = new window.Web3Modal.default({
      cacheProvider: false,
      providerOptions: {
        walletconnect: {
          package: window.WalletConnectProvider.default,
          options: {
            infuraId: '27e484dcd9e3efcfd25a83a78777cdf1' // demo Infura ID
          }
        }
      }
    });
  }

  initWeb3Modal();

  // Connect wallet
  async function onConnectWallet() {
    try {
      provider = await web3Modal.connect();
      ethersProvider = new ethers.providers.Web3Provider(provider);
      const signer = ethersProvider.getSigner();
      walletAddress = await signer.getAddress();
      isWalletConnected = true;

      walletInfo.style.display = 'block';
      walletInfo.textContent = `Connected wallet: ${walletAddress}`;

      connectWalletBtn.textContent = 'Disconnect Wallet';
      connectWalletBtn.setAttribute('aria-pressed', 'true');

      updateReferralLink();
      enableAllButtonsOnConnect();

      loadUserData();

      // Listen for account changes or disconnect
      if(provider.on) {
        provider.on('accountsChanged', (accounts) => {
          if(accounts.length === 0) {
            onDisconnectWallet();
          } else {
            walletAddress = accounts[0];
            loadUserData();
          }
        });
        provider.on('disconnect', () => {
          onDisconnectWallet();
        });
      }
    } catch (error) {
      alert('Could not connect wallet: ' + error.message);
    }
  }

  // Disconnect wallet
  async function onDisconnectWallet() {
    try {
      if(provider?.disconnect) await provider.disconnect();
    } catch {}
    provider = null;
    ethersProvider = null;
    walletAddress = null;
    isWalletConnected = false;

    walletInfo.style.display = 'none';
    walletInfo.textContent = '';
    connectWalletBtn.textContent = 'Connect Wallet';
    connectWalletBtn.setAttribute('aria-pressed', 'false');

    disableAllButtonsOnDisconnect();

    // Clear states and UI
    clearUserData();
  }

  connectWalletBtn.addEventListener('click', () => {
    if(isWalletConnected) onDisconnectWallet();
    else onConnectWallet();
  });

  // Enable controls on wallet connect
  function enableAllButtonsOnConnect() {
    stakeBtn.disabled = false;
    activateBoosterBtn.disabled = false;
    copyReferralBtn.disabled = false;
    farmActionBtn.disabled = false;

    stakeBtn.setAttribute('aria-disabled', 'false');
    activateBoosterBtn.setAttribute('aria-disabled', 'false');
    copyReferralBtn.setAttribute('aria-disabled', 'false');
    farmActionBtn.setAttribute('aria-disabled', 'false');
  }

  // Disable controls on wallet disconnect
  function disableAllButtonsOnDisconnect() {
    stakeBtn.disabled = true;
    activateBoosterBtn.disabled = true;
    copyReferralBtn.disabled = true;
    farmActionBtn.disabled = true;

    stakeBtn.setAttribute('aria-disabled', 'true');
    activateBoosterBtn.setAttribute('aria-disabled', 'true');
    copyReferralBtn.setAttribute('aria-disabled', 'true');
    farmActionBtn.setAttribute('aria-disabled', 'true');
  }

  // Referral link update
  function updateReferralLink() {
    if(walletAddress) {
      referralLink = `https://okapitoken.example.com/?ref=${walletAddress}`;
      referralLinkInput.value = referralLink;
      copyReferralBtn.disabled = false;
    } else {
      referralLinkInput.value = '';
      copyReferralBtn.disabled = true;
    }
  }

  copyReferralBtn.addEventListener('click', () => {
    if(!referralLinkInput.value) return;
    navigator.clipboard.writeText(referralLinkInput.value)
      .then(() => alert('Referral link copied to clipboard!'))
      .catch(() => alert('Failed to copy referral link.'));
  });

  // Stake input validation & enabling button
  stakeInput.addEventListener('input', () => {
    const valid = isWalletConnected && stakeInput.value && Number(stakeInput.value) > 0;
    stakeBtn.disabled = !valid;
    stakeBtn.setAttribute('aria-disabled', !valid ? 'true' : 'false');
  });

  // Stake form submit handler (mocked staking)
  document.getElementById('stake-form').addEventListener('submit', e => {
    e.preventDefault();
    const val = parseFloat(stakeInput.value);
    if(isWalletConnected && val > 0) {
      stakedAmount += val;
      stakedAmountSpan.textContent = stakedAmount.toFixed(4);
      stakedInfo.style.display = 'block';
      stakeInput.value = '';
      stakeBtn.disabled = true;
      stakeBtn.setAttribute('aria-disabled', 'true');
      alert(`Successfully staked ${val} $OKAPI Tokens!`);
      saveUserData(); 
      updateDailyTaskStatus();
      updateFarmActionUI();
    } else {
      alert("Connect your wallet and enter a valid amount to stake.");
    }
  });

  // Booster selection
  let selectedBooster = null;

  function clearBoosterSelection() {
    boosters.forEach(b => {
      b.classList.remove('selected');
      b.setAttribute('aria-pressed', 'false');
    });
    selectedBooster = null;
    activateBoosterBtn.disabled = true;
    activateBoosterBtn.setAttribute('aria-disabled', 'true');
  }

  boosters.forEach(boost => {
    boost.addEventListener('click', () => {
      if(!isWalletConnected) return alert("Connect wallet to activate boosters.");
      clearBoosterSelection();
      boost.classList.add('selected');
      boost.setAttribute('aria-pressed', 'true');
      selectedBooster = {
        multiplier: parseFloat(boost.dataset.multiplier),
        name: boost.querySelector('h3').textContent.trim()
      };
      activateBoosterBtn.disabled = false;
      activateBoosterBtn.setAttribute('aria-disabled', 'false');
    });
    boost.addEventListener('keydown', e => {
      if(e.key === "Enter" || e.key === " ") {
        e.preventDefault();
        boost.click();
      }
    });
  });

  activateBoosterBtn.addEventListener('click', () => {
    if(selectedBooster) {
      activeBooster = selectedBooster;
      activeBoosterInfo.textContent = `${activeBooster.name} (${activeBooster.multiplier}x)`;
      activeBoosterInfoBox.style.display = 'block';
      alert(`Activated booster: ${activeBooster.name} - Rewards multiplied by ${activeBooster.multiplier}x`);
      clearBoosterSelection();
      saveUserData();
      updateDailyTaskStatus();
      updateFarmActionUI();
    }
  });

  // Farming level display
  function updateLevelDisplay() {
    levelValueSpan.textContent = farmingLevel;
  }

  // Invite stats - mock
  function updateInviteStats() {
    if(walletAddress) {
      totalInvites = Number(localStorage.getItem(walletAddress + '_okapi_invites')) || Math.floor(Math.random() * 10);
      earnedBonuses = Number(localStorage.getItem(walletAddress + '_okapi_bonuses')) || (totalInvites * 5);
      totalInvitesSpan.textContent = totalInvites;
      earnedBonusesSpan.textContent = earnedBonuses.toFixed(2);
    } else {
      totalInvitesSpan.textContent = '0';
      earnedBonusesSpan.textContent = '0';
    }
  }

  // Daily Tasks - mock tasks with level and farming session completion
  const tasks = [
    { id: 'task1', description: 'Stake at least 50 $OKAPI Tokens', completed: false },
    { id: 'task2', description: 'Invite 3 friends', completed: false },
    { id: 'task3', description: 'Activate a Booster', completed: false },
    { id: 'task4', description: 'Connect your wallet', completed: false },
    { id: 'task5', description: 'Complete a 3-hour farming session', completed: false }
  ];

  function updateDailyTaskStatus() {
    if(!isWalletConnected) return;
    tasks.forEach(task => {
      switch(task.id) {
        case 'task1':
          task.completed = stakedAmount >= 50;
          break;
        case 'task2':
          task.completed = totalInvites >= 3;
          break;
        case 'task3':
          task.completed = activeBooster !== null;
          break;
        case 'task4':
          task.completed = isWalletConnected;
          break;
        case 'task5':
          task.completed = farmingSessionsCompleted > 0;
          break;
      }
    });
    renderTaskList();
  }

  function clearDailyTaskCompletion() {
    tasks.forEach(t => t.completed = false);
    renderTaskList();
  }

  function renderTaskList() {
    taskList.innerHTML = '';
    tasks.forEach(task => {
      const li = document.createElement('li');
      li.textContent = task.description + ' ';
      if(task.completed) {
        const doneSpan = document.createElement('span');
        doneSpan.textContent = '✅';
        doneSpan.setAttribute('aria-label', 'Task completed');
        li.appendChild(doneSpan);
      } else {
        const btn = document.createElement('button');
        btn.textContent = 'Complete';
        btn.disabled = true;
        btn.setAttribute('aria-disabled', 'true');
        btn.setAttribute('aria-label', 'Task incomplete');
        li.appendChild(btn);
      }
      taskList.appendChild(li);
    });
  }

  // Save all user data for persistence in localStorage keyed by walletAddress
  function saveUserData() {
    if(!walletAddress) return;
    localStorage.setItem(walletAddress + '_stakedAmount', stakedAmount);
    localStorage.setItem(walletAddress + '_activeBooster', JSON.stringify(activeBooster));
    localStorage.setItem(walletAddress + '_farmingState', JSON.stringify(farmingState));
    localStorage.setItem(walletAddress + '_farmingLevel', farmingLevel);
    localStorage.setItem(walletAddress + '_farmingSessionsCompleted', farmingSessionsCompleted);
  }
  // Load user data from localStorage
  function loadUserData() {
    if(!walletAddress) return;

    // Load staked amount
    const sa = localStorage.getItem(walletAddress + '_stakedAmount');
    stakedAmount = sa ? parseFloat(sa) : 0;
    if(stakedAmount > 0) {
      stakedAmountSpan.textContent = stakedAmount.toFixed(4);
      stakedInfo.style.display = 'block';
    } else {
      stakedInfo.style.display = 'none';
    }

    // Load booster
    const ab = localStorage.getItem(walletAddress + '_activeBooster');
    if(ab) {
      try {
        activeBooster = JSON.parse(ab);
        if(activeBooster && activeBooster.name && activeBooster.multiplier) {
          activeBoosterInfo.textContent = `${activeBooster.name} (${activeBooster.multiplier}x)`;
          activeBoosterInfoBox.style.display = 'block';
        } else {
          activeBooster = null;
          activeBoosterInfoBox.style.display = 'none';
        }
      } catch {
        activeBooster = null;
        activeBoosterInfoBox.style.display = 'none';
      }
    } else {
      activeBooster = null;
      activeBoosterInfoBox.style.display = 'none';
    }

    // Load farming state
    const fs = localStorage.getItem(walletAddress + '_farmingState');
    if(fs) {
      try {
        const temp = JSON.parse(fs);
        if(temp && ('startTimestamp' in temp) && ('collectedRewards' in temp)) {
          farmingState = temp;
        } else {
          farmingState = {startTimestamp:null, collectedRewards:false};
        }
      } catch {
        farmingState = {startTimestamp:null, collectedRewards:false};
      }
    } else {
      farmingState = {startTimestamp:null, collectedRewards:false};
    }

    // Load farming level
    const lvl = localStorage.getItem(walletAddress + '_farmingLevel');
    farmingLevel = lvl ? Number(lvl) : 1;
    if(farmingLevel < 1) farmingLevel = 1;
    updateLevelDisplay();

    // Load farming sessions completed
    const fsc = localStorage.getItem(walletAddress + '_farmingSessionsCompleted');
    farmingSessionsCompleted = fsc ? Number(fsc) : 0;

    updateReferralLink();
    updateInviteStats();
    updateDailyTaskStatus();
    updateFarmActionUI();
  }

  // Clear data on disconnect
  function clearUserData() {
    stakedAmount = 0;
    activeBooster = null;
    farmingState = {startTimestamp:null, collectedRewards:false};
    farmingLevel = 1;
    farmingSessionsCompleted = 0;
    stakedAmountSpan.textContent = '0';
    stakedInfo.style.display = 'none';
    activeBoosterInfo.textContent = 'None';
    activeBoosterInfoBox.style.display = 'none';
    farmStatusDiv.textContent = '';
    farmTimerDiv.textContent = '';
    farmActionBtn.textContent = 'Tapping';
    farmActionBtn.disabled = true;
    farmActionBtn.setAttribute('aria-disabled', 'true');
    updateLevelDisplay();
    updateReferralLink();
    updateInviteStats();
    clearDailyTaskCompletion();
  }

  // Farm timer UI update
  function updateFarmActionUI() {
    if(!isWalletConnected) {
      farmStatusDiv.textContent = 'Connect your wallet to start farming.';
      farmTimerDiv.textContent = '';
      farmActionBtn.textContent = 'Tapping';
      farmActionBtn.disabled = true;
      farmActionBtn.setAttribute('aria-disabled', 'true');
      return;
    }

    if(farmingState.startTimestamp === null) {
      farmStatusDiv.textContent = 'You have no active farming session.';
      farmTimerDiv.textContent = '';
      farmActionBtn.textContent = 'Tapping';
      farmActionBtn.disabled = false;
      farmActionBtn.setAttribute('aria-disabled', 'false');
      return;
    }
    
    const now = Date.now();
    const elapsed = now - farmingState.startTimestamp;

    if(elapsed < FARM_DURATION_MS) {
      const remaining = FARM_DURATION_MS - elapsed;
      farmStatusDiv.textContent = 'Farming in progress. Time remaining:';
      farmTimerDiv.textContent = formatTime(remaining);
      farmActionBtn.textContent = 'Farming...';
      farmActionBtn.disabled = true;
      farmActionBtn.setAttribute('aria-disabled', 'true');
    } else {
      if(!farmingState.collectedRewards) {
        farmStatusDiv.textContent = 'Farming session completed! Collect your rewards.';
        farmTimerDiv.textContent = '';
        farmActionBtn.textContent = 'Collect Rewards';
        farmActionBtn.disabled = false;
        farmActionBtn.setAttribute('aria-disabled', 'false');
      } else {
        farmStatusDiv.textContent = 'Rewards collected. Start a new farming session.';
        farmTimerDiv.textContent = '';
        farmActionBtn.textContent = 'Tapping';
        farmActionBtn.disabled = false;
        farmActionBtn.setAttribute('aria-disabled', 'false');
      }
    }
  }

  // Format milliseconds to HH:MM:SS
  function formatTime(ms) {
    if(ms <= 0) return '00:00:00';
    const totalSeconds = Math.floor(ms / 1000);
    const hh = Math.floor(totalSeconds / 3600).toString().padStart(2, '0');
    const mm = Math.floor((totalSeconds % 3600) / 60).toString().padStart(2, '0');
    const ss = (totalSeconds % 60).toString().padStart(2, '0');
    return `${hh}:${mm}:${ss}`;
  }

  // Farm action button click handler
  farmActionBtn.addEventListener('click', () => {
    if(!isWalletConnected) {
      alert('Please connect your wallet first.');
      return;
    }
    if(farmingState.startTimestamp === null || (farmingState.collectedRewards && new Date() - farmingState.startTimestamp >= FARM_DURATION_MS)) {
      // Start farming
      farmingState.startTimestamp = Date.now();
      farmingState.collectedRewards = false;
      alert('Farming session started! Come back in 3 hours to collect your rewards.');
      saveUserData();
      updateFarmActionUI();
    } else if(!farmingState.collectedRewards) {
      // Try to collect rewards
      const now = Date.now();
      const elapsed = now - farmingState.startTimestamp;
      if(elapsed >= FARM_DURATION_MS) {
        // Compute rewards based on staking, booster, and level
        // Base 5% per 3 hours farming on staked amount, booster multiplier, plus +2% bonus per level above 1
        let rewards = stakedAmount * 0.05;
        if(activeBooster) rewards *= activeBooster.multiplier;
        const levelBonusMultiplier = 1 + ((farmingLevel - 1) * 0.02);
        rewards *= levelBonusMultiplier;
        rewards = Math.max(0, rewards).toFixed(4);

        alert(`🎉 You collected ${rewards} $OKAPI Tokens as farming rewards! Your farming level has increased.`);

        farmingState.collectedRewards = true;
        farmingSessionsCompleted++;
        farmingLevel = Math.min(100, farmingLevel + 1); // max level 100
        saveUserData();
        updateLevelDisplay();
        updateDailyTaskStatus();
        updateFarmActionUI();
      } else {
        alert('Farming session is not yet complete. Please wait for timer to finish.');
      }
    } else {
      // Farming session ended & rewards collected, starting a new farming session
      farmingState.startTimestamp = Date.now();
      farmingState.collectedRewards = false;
      alert('New farming session started! Come back in 3 hours to collect your rewards.');
      saveUserData();
      updateFarmActionUI();
    }
  });

  // Timer refresh interval - update timer every 1 second
  setInterval(() => {
    if(isWalletConnected && farmingState.startTimestamp !== null && !farmingState.collectedRewards) {
      updateFarmActionUI();
    }
  }, 1000);

  // Load user data helper
  function loadFullUserData() {
    loadUserData();
    updateLevelDisplay();
  }

  // Initialize farming level display
  updateLevelDisplay();

})();
</script>
</body>
</html>
