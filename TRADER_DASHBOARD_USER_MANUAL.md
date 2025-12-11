# G-SignalX-M19-Trading-System - User Manual

## 📋 Table of Contents
1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Dashboard Overview](#dashboard-overview)
4. [Trading Styles & Dashboard Use](#trading-styles--dashboard-use)
5. [Session-Based Trading](#session-based-trading)
6. [Configuration Settings](#configuration-settings)
7. [Advanced Features](#advanced-features)
8. [Risk Management](#risk-management)
9. [Troubleshooting](#troubleshooting)
10. [Best Practices](#best-practices)

---

## 🎯 Introduction

The **G-SignalX Forex Trading Dashboard** is an automated trading system that executes trades based on market sessions (Tokyo & Sydney, London, New York) with a comprehensive web-based interface for configuration, monitoring, and session management.

### Key Features
- **Automated Session-Based Trading**: Executes trades automatically when market sessions become active
- **Real-time Monitoring**: Live dashboard with session status and trading activities
- **Multi-Style Support**: Configurable for scalping, day trading, swing trading, and position trading
- **Risk Management**: Built-in profit monitoring and position management
- **36+ Currency Pairs**: Support for major, minor, with cross currency pairs and crypto pairs

---

## 🚀 Getting Started

### Prerequisites
- **Python 3.13.3** (compatible with MetaTrader 5 Python wrapper) or higher  
  [Download Python](https://www.python.org/downloads/)  
  [Direct link to Python 3.13.10](https://www.python.org/downloads/release/python-31310/)
- **MetaTrader 5 Terminal**: Must be installed and running
- **Valid Forex Broker Account**: With MT5 access
- **Web Browser**: Chrome, Firefox, Safari, or Edge
- **Stable Internet Connection**: For real-time data

---

### Installation Steps

#### 1. **Clone the Repository or Unzip the Files**
```bash
git clone <repository-url>
# Or unzip the downloaded archive
cd <project-folder>
```

#### 2. **Create a Virtual Environment**
```bash
python -m venv .venv

# On Windows (Preferred)
.venv\Scripts\activate

# On macOS/Linux
source .venv/bin/activate
```

#### 3. **Install Dependencies**
```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

#### 4. **Set Up Environment Variables**
Create a `.env` file in the project root:
```bash
echo "APP_USERNAME=admin" > .env
echo "APP_PASSWORD=your_secure_password" >> .env
echo "SECRET_KEY=your_secret_key_here" >> .env
echo "SESSION_TIMEOUT=15" >> .env
```

#### 5. **Initialize the Database**
```bash
python setup_db.py
```



### Accessing the In‑App User Manual
- In the dashboard header (next to the Logout button), click **User Manual** to open a responsive, standalone help page.
- The manual uses collapsible accordions for clarity and is fully mobile‑friendly.

---

## 📊 Dashboard Overview

### Main Interface Components

#### 1. **Brand Header**
- **Company Branding**: G-SignalX (Forex) Trading Dashboard
- **Real-time Clock**: Current time display
- **User Welcome**: Shows logged-in username
- **Logout Button**: Secure session termination

#### 2. **Quick Info Bar**
- **Live Indicator**: Real-time system status
- **Current Time**: Local timezone display
- **Active Sessions**: Currently active trading sessions
- **System Status**: Trading bot status indicators

#### 3. **Trading Sessions Panel**
- **Session Status**: Active/inactive indicators
- **Time Ranges**: Session start/end times
- **Currency Pairs**: Configured pairs for each session
- **Trading Directions**: Buy/Sell/Neutral settings

#### 4. **Account Information Panel**
- **Account Balance**: Current account balance
- **Profit/Loss**: Real-time P&L display
- **Open Positions**: Number of active positions
- **Last Update**: Timestamp of last data refresh

#### 5. **Quick Actions Panel**
- **Emergency Stop**: Immediately halt all trading
- **Refresh Data**: Update account information
- **Settings Access**: Quick access to configuration
- **Logs View**: View trading activity logs

#### 6. **User Manual Button**
- Located at the top‑right of the header beside Logout.
- Opens a standalone, mobile‑friendly guide with toggles/accordions.

---

## 🧠 Trading Styles & Dashboard Use

### 1. **Scalping**
**Definition**: Enter and exit trades within minutes.

**Goal**: Capture small price moves with high speed and precision.

**Best For**: Fast-moving markets and traders who can monitor closely.

#### Dashboard Configuration for Scalping:
```
Trading Settings:
- Volume: 0.01-0.05 lots (small positions)
- Scalp Multiplier: 0.3-0.5 (reduced position size)
- Base Entry Pips: 1-2 pips
- Order Expiry: 2-5 minutes
- Session Check Interval: 1-2 seconds

Profit Monitor Settings:
- Min Profit %: 0.1-0.3%
- Trailing Stop %: 0.05-0.1%
- Check Interval: 5-10 seconds
- Partial Close: Enabled (50% at 0.2% profit)
```

#### Session Strategy for Scalping:
- **Tokyo & Sydney**: Focus on JPY pairs (USDJPY, EURJPY)
- **London**: Major pairs (EURUSD, GBPUSD)
- **London-NY Overlap**: High volatility pairs
- **New York**: USD pairs and crosses

#### Dashboard Usage:
1. **Monitor Active Sessions**: Watch for session transitions
2. **Quick Direction Changes**: Rapidly adjust pair directions
3. **Real-time Profit Tracking**: Monitor small profit targets
4. **Emergency Controls**: Use emergency stop for rapid exits

### 2. **Day Trading**
**Definition**: Trades are held from minutes to hours, closed before market close.

**Goal**: Capture intra-day moves based on technical signals and trends.

**Best For**: Traders who can dedicate full attention during the trading day.

#### Dashboard Configuration for Day Trading:
```
Trading Settings:
- Volume: 0.05-0.2 lots (moderate positions)
- Scalp Multiplier: 0.7-1.0 (standard position size)
- Base Entry Pips: 3-5 pips
- Order Expiry: 10-15 minutes
- Session Check Interval: 5-10 seconds

Profit Monitor Settings:
- Min Profit %: 0.5-1.0%
- Trailing Stop %: 0.2-0.5%
- Check Interval: 15-30 seconds
- Partial Close: Enabled (30% at 0.8% profit)
```

#### Session Strategy for Day Trading:
- **Tokyo & Sydney**: Asian session momentum
- **London**: European session trends
- **London-NY Overlap**: Major trend reversals
- **New York**: US session momentum

#### Dashboard Usage:
1. **Session Planning**: Pre-configure sessions before they start
2. **Trend Analysis**: Use session overlap periods for trend confirmation
3. **Position Management**: Monitor multiple positions throughout the day
4. **End-of-Day Review**: Close positions before session end

### 3. **Swing Trading**
**Definition**: Trades held for hours or days, occasionally weeks and months.

**Goal**: Catch larger moves across short- to mid-term trends.

**Best For**: Part-time traders or those analyzing market sentiment and trend shifts.

#### Dashboard Configuration for Swing Trading:
```
Trading Settings:
- Volume: 0.1-0.5 lots (larger positions)
- Scalp Multiplier: 1.0-1.5 (increased position size)
- Base Entry Pips: 10-20 pips
- Order Expiry: 30-60 minutes
- Session Check Interval: 30-60 seconds

Profit Monitor Settings:
- Min Profit %: 1.0-3.0%
- Trailing Stop %: 0.5-1.0%
- Check Interval: 60-120 seconds
- Partial Close: Enabled (25% at 2.0% profit)
```

#### Session Strategy for Swing Trading:
- **Tokyo & Sydney**: Long-term Asian trends
- **London**: European trend establishment
- **London-NY Overlap**: Major trend continuation
- **New York**: US trend confirmation

#### Dashboard Usage:
1. **Weekly Planning**: Set up weekly trading strategies
2. **Trend Confirmation**: Use multiple sessions for trend validation
3. **Position Scaling**: Add to positions across sessions
4. **Risk Management**: Monitor larger position sizes

### 4. **Position Trading**
**Definition**: Trades target entries and exits from swing pullbacks; enter and manage swings for weeks to months, based on long‑term trends.

**Goal**: Enter major trend positions using signals confirmed by higher timeframes.

**Best For**: Traders using day or swing setups as entry points for bigger‑picture strategies.

#### Dashboard Configuration for Position Trading:
```
Trading Settings:
- Volume: 0.2-1.0 lots (large positions)
- Scalp Multiplier: 1.5-2.0 (maximum position size)
- Base Entry Pips: 30-50 pips
- Order Expiry: 120-240 minutes
- Session Check Interval: 300-600 seconds

Profit Monitor Settings:
- Min Profit %: 3.0-10.0%
- Trailing Stop %: 1.0-3.0%
- Check Interval: 300-600 seconds
- Partial Close: Enabled (20% at 5.0% profit)
```

#### Session Strategy for Position Trading:
- **Tokyo & Sydney**: Long-term Asian market trends
- **London**: European market cycles
- **London-NY Overlap**: Global trend establishment
- **New York**: US market leadership

#### Dashboard Usage:
1. **Monthly Planning**: Set up monthly trading strategies
2. **Fundamental Analysis**: Combine with economic calendar
3. **Position Building**: Accumulate positions over time
4. **Portfolio Management**: Monitor multiple long-term positions

---

## 👤 User Types & Signal‑Based Workflows

Use the dashboard to place and manage trades regardless of how you generate signals:

### A. Experienced Chart Analyst (Manual TA)
- Perform your analysis on external charts, then map decisions into the dashboard:
  - Set session pair directions (Buy/Sell/Neutral)
  - Choose volume and base entry pips
  - Use Profit Monitor for partials and trailing
  - Optionally set total daily target via Profit Scouting

### B. Signal‑Only Users (Entry Signals)
- Your system tells you when to enter; dashboard manages exits:
  - Flip session pair direction to Buy/Sell on incoming signal
  - Enable tight trailing and partial closes in Profit Monitor
  - Use Profit Scouting for total profit caps across positions

### C. Signals with SL/TP Users (Full Signals)
- Your provider includes entry, stop loss, and take profit:
  - Mirror the signal; set order deviation tolerance in Profit Scouting
  - Keep Profit Monitor enabled to secure early partial profits
  - Use total target profit to lock a profitable day and stop

Tip: Smart Trading = Trend Alignment + Signal Confirmation + Risk Awareness.

---

## 🤖 Standalone Bots: Strategic Utilities

Both bots are fast and can be used by any trader type to maximize trade outcomes.

### Profit Managing Bot Program
Designed to automate and manage trading positions, aiming to maximize profits by closing positions when they reach certain profit thresholds. It includes:
- **Market Status Check**: Verifies if the market is open for the trading symbol
- **Volume Normalization**: Adjusts trade volumes to broker limits
- **Position Management**: Retrieves open positions and calculates profit percentages
- **Filling Mode Determination**: Picks appropriate order filling mode
- **Position Closing**: Full or partial closes with retry logic on failure
- **Main Monitoring Loop**: Continuous, configurable checking and management

Best use cases:
- Secure partials on scalps and intraday moves
- Enforce a trailing stop policy across all positions
- Normalize volume automatically for diverse symbols

### Profit Scouting Bot Program
Monitors and manages positions using MT5 to close when profit conditions are met, optimizing outcomes.
- **Automated Monitoring**: Detects positions meeting per‑pair or per‑position targets
- **Config‑Driven**: Centralized settings for consistency
- **ProfitMonitor Core**: Determines which positions to close at predefined targets
- **Stable Connectivity**: Ensures a reliable account connection

Best use cases:
- Daily “total profit” objective with auto‑stop
- Signal users who want objective exits regardless of emotion
- Position traders who want staged profit locking

---

## ⏰ Session-Based Trading
---

## ⚠️ Risk Awareness

Traders should always monitor:

- 📉 **Account Drawdown**: Know risk tolerance and exposure; cap daily loss
- 📰 **High‑Impact News**: Economic events can override technical signals
- 🕒 **Market Sessions & Volatility Spikes**: Be aware of London/NY opens and overlaps

### 🎯 Trader Focus Point for Signal‑Based Decisions
When using a signal system like G‑SignalX, focus on:

- ✅ Signal alignment across multiple timeframes
- ✅ Trend confirmation from higher timeframes
- ✅ Avoiding trades during major news or session volatility
- ✅ Strict risk control based on account size and signal strength

Smart Trading = Trend Alignment + Signal Confirmation + Risk Awareness

### Trading Sessions Overview

#### 1. **Tokyo & Sydney Session**
- **Time**: 22:00 - 07:00 UTC
- **Volatility Factor**: 1.2x
- **Best Pairs**: JPY crosses, AUD pairs
- **Characteristics**: Asian market momentum

#### 2. **Tokyo-London Overlap**
- **Time**: 07:00 - 09:00 UTC
- **Volatility Factor**: 1.5x
- **Best Pairs**: EUR/JPY, GBP/JPY
- **Characteristics**: High volatility transition

#### 3. **London Session**
- **Time**: 09:00 - 13:00 UTC
- **Volatility Factor**: 1.3x
- **Best Pairs**: EUR/USD, GBP/USD
- **Characteristics**: European market dominance

#### 4. **London-NY Overlap**
- **Time**: 13:00 - 16:00 UTC
- **Volatility Factor**: 1.6x
- **Best Pairs**: All major pairs
- **Characteristics**: Highest volatility period

#### 5. **New York Session**
- **Time**: 16:00 - 22:00 UTC
- **Volatility Factor**: 1.3x
- **Best Pairs**: USD crosses
- **Characteristics**: US market leadership

### Currency Pairs Configuration

#### Major Pairs
- **EUR/USD**: Euro vs US Dollar
- **GBP/USD**: British Pound vs US Dollar
- **USD/JPY**: US Dollar vs Japanese Yen
- **USD/CHF**: US Dollar vs Swiss Franc
- **USD/CAD**: US Dollar vs Canadian Dollar

#### Minor Pairs
- **AUD/USD**: Australian Dollar vs US Dollar
- **NZD/USD**: New Zealand Dollar vs US Dollar
- **EUR/GBP**: Euro vs British Pound
- **EUR/JPY**: Euro vs Japanese Yen
- **GBP/JPY**: British Pound vs Japanese Yen

#### Cross Pairs
- **CHF/JPY**: Swiss Franc vs Japanese Yen
- **CAD/JPY**: Canadian Dollar vs Japanese Yen
- **AUD/JPY**: Australian Dollar vs Japanese Yen
- **GBP/CHF**: British Pound vs Swiss Franc
- **EUR/CHF**: Euro vs Swiss Franc

### Setting Trading Directions

#### For Each Session:
1. **Select Session**: Click on the session name
2. **Choose Pair**: Select currency pair from dropdown
3. **Set Direction**:
   - **Buy**: Opens long position when session activates
   - **Sell**: Opens short position when session activates
   - **Neutral**: No trading for this pair in this session
4. **Save Configuration**: Click save to apply changes

---

## ⚙️ Configuration Settings

### Trading Bot Settings

#### Volume Management
- **Volume (Lots)**: Standard lot size per trade
  - **Scalping**: 0.01-0.05
  - **Day Trading**: 0.05-0.2
  - **Swing Trading**: 0.1-0.5
  - **Position Trading**: 0.2-1.0

#### Scalping Configuration
- **Scalp Multiplier**: Reduces position size for scalping
  - **Range**: 0.1-2.0
  - **Recommended**: 0.3-0.5 for scalping

#### Entry Management
- **Base Entry Pips**: Distance for entry orders
  - **Scalping**: 1-2 pips
  - **Day Trading**: 3-5 pips
  - **Swing Trading**: 10-20 pips
  - **Position Trading**: 30-50 pips

#### Order Management
- **Min Spread Multiplier**: Minimum spread requirement
- **Order Expiry**: Time limit for pending orders
- **Session Check Interval**: Frequency of session monitoring

### Profit Monitor Settings

#### Profit Targets
- **Min Profit %**: Minimum profit before taking action
- **Target Profit Pair**: Target profit per currency pair
- **Target Profit Position**: Target profit per individual position
- **Total Target Profit**: Overall profit target

#### Risk Management
- **Trailing Stop %**: Dynamic stop-loss percentage
- **Partial Close Enabled**: Enable partial position closing
- **Partial Close Threshold**: Profit level for partial close
- **Partial Close %**: Percentage of position to close

#### Monitoring
- **Check Interval**: Frequency of profit monitoring
- **Max Retries**: Maximum retry attempts
- **Retry Delay**: Delay between retries
- **Enable Market Check**: Market condition validation

### Profit Scouting Settings

#### Profit Targeting
- **Target Profit Pair ($)**: Dollar target per pair
- **Target Profit Position ($)**: Dollar target per position
- **Total Target Profit ($)**: Overall dollar target

#### Monitoring
- **Check Interval**: Frequency of profit scouting
- **Order Deviation**: Allowed price deviation
- **Magic Number**: Trade identification number

---

## 🔧 Advanced Features

### Real-time Monitoring

#### Live Indicators
- **System Status**: Green/red status indicators
- **Session Activity**: Active session highlighting
- **Position Count**: Real-time position updates
- **Profit Tracking**: Live P&L updates

#### Data Refresh
- **Auto-refresh**: Automatic data updates
- **Manual Refresh**: Manual data refresh button
- **Update Frequency**: Configurable refresh intervals

### Emergency Controls

#### Emergency Stop
- **Immediate Halt**: Stops all trading activities
- **Position Protection**: Protects existing positions
- **System Reset**: Resets trading system state

#### Manual Override
- **Position Management**: Manual position adjustments
- **Order Cancellation**: Cancel pending orders
- **System Restart**: Restart trading components

### Logging and Analytics

#### Activity Logs
- **Trading Logs**: All trading activities
- **Error Logs**: System errors and warnings
- **Security Logs**: Login and access attempts
- **Performance Logs**: System performance metrics

#### Analytics Dashboard
- **Performance Metrics**: Win rate, profit factor
- **Session Analysis**: Session-specific performance
- **Pair Performance**: Currency pair analysis
- **Risk Metrics**: Drawdown, Sharpe ratio

---

## 🛡️ Risk Management

### Position Sizing

#### Risk Per Trade
- **1% Rule**: Risk maximum 1% of account per trade
- **2% Rule**: Risk maximum 2% of account per trade
- **5% Rule**: Risk maximum 5% of account per trade

#### Volume Calculation
```
Risk Amount = Account Balance × Risk Percentage
Position Size = Risk Amount ÷ Stop Loss Distance
```

### Stop Loss Management

#### Fixed Stop Loss
- **Pip-based**: Fixed number of pips
- **Percentage-based**: Fixed percentage of account
- **ATR-based**: Based on Average True Range

#### Trailing Stop Loss
- **Dynamic Adjustment**: Moves with price
- **Lock-in Profits**: Protects winning trades
- **Risk Reduction**: Reduces risk as profit increases

### Profit Taking

#### Partial Close Strategy
- **25% at 1R**: Close 25% at 1:1 risk-reward
- **50% at 2R**: Close 50% at 2:1 risk-reward
- **25% at 3R**: Close remaining at 3:1 risk-reward

#### Full Close Strategy
- **Target-based**: Close at specific profit targets
- **Time-based**: Close after specific time period
- **Signal-based**: Close on technical signals

### Correlation Management

#### Currency Pair Correlation
- **Positive Correlation**: EUR/USD and GBP/USD
- **Negative Correlation**: EUR/USD and USD/CHF
- **Low Correlation**: EUR/USD and AUD/JPY

#### Risk Reduction
- **Limit Correlated Pairs**: Maximum 2-3 correlated pairs
- **Diversify Sessions**: Spread positions across sessions
- **Monitor Exposure**: Track total exposure per currency

---

## 🔍 Troubleshooting

### Common Issues

#### Connection Problems
**Issue**: Cannot connect to MetaTrader 5
**Solution**:
1. Ensure MT5 is running
2. Check login credentials
3. Verify server connection
4. Restart trading bot

#### Session Not Activating
**Issue**: Trading session not starting automatically
**Solution**:
1. Check session time configuration
2. Verify timezone settings
3. Check session status indicators
4. Restart session monitoring

#### Orders Not Executing
**Issue**: Orders not being placed
**Solution**:
1. Check account balance
2. Verify market hours
3. Check spread requirements
4. Review order parameters

#### Profit Monitor Not Working
**Issue**: Profit monitoring not functioning
**Solution**:
1. Check profit settings
2. Verify position data
3. Check monitoring intervals
4. Review log files

### Error Messages

#### "MT5 Connection Failed"
- **Cause**: MetaTrader 5 not running or connection issues
- **Solution**: Restart MT5 and trading bot

#### "Insufficient Balance"
- **Cause**: Account balance too low for position size
- **Solution**: Reduce volume or add funds

#### "Market Closed"
- **Cause**: Trading outside market hours
- **Solution**: Check market hours and session times

#### "Invalid Parameters"
- **Cause**: Incorrect configuration settings
- **Solution**: Review and correct parameter values

### Performance Issues

#### Slow Dashboard
- **Cause**: High system load or network issues
- **Solution**: Refresh page, check internet connection

#### Delayed Updates
- **Cause**: Slow data feed or system overload
- **Solution**: Check data provider, restart system

#### High CPU Usage
- **Cause**: Multiple bots running or system overload
- **Solution**: Optimize settings, reduce monitoring frequency

---

## 📚 Best Practices

### General Trading

#### 1. **Start Small**
- Begin with demo account
- Use small position sizes
- Test all features thoroughly
- Gradually increase exposure

#### 2. **Risk Management First**
- Set strict risk limits
- Use proper position sizing
- Implement stop losses
- Monitor correlation exposure

#### 3. **Session Planning**
- Plan sessions in advance
- Set realistic targets
- Monitor session transitions
- Adjust strategies as needed

#### 4. **Regular Monitoring**
- Check system status daily
- Review performance weekly
- Monitor risk metrics
- Update strategies monthly

### Configuration Best Practices

#### 1. **Conservative Settings**
- Start with lower volumes
- Use wider stops initially
- Set realistic profit targets
- Enable all safety features

#### 2. **Gradual Optimization**
- Test one change at a time
- Monitor results carefully
- Keep detailed records
- Document successful settings

#### 3. **Backup Configurations**
- Save working configurations
- Document parameter changes
- Keep multiple strategy files
- Regular configuration backups

### Advanced Strategies

#### 1. **Multi-Session Approach**
- Combine session strategies
- Use overlap periods effectively
- Monitor session correlations
- Adjust for market conditions

#### 2. **Dynamic Adjustments**
- Adapt to market volatility
- Adjust for news events
- Modify for trend changes
- Optimize for market phases

#### 3. **Portfolio Management**
- Diversify across pairs
- Balance session exposure
- Monitor total risk
- Rebalance regularly

### Maintenance and Updates

#### 1. **Regular Maintenance**
- Update system regularly
- Check for new features
- Review performance data
- Optimize configurations

#### 2. **Continuous Learning**
- Study market behavior
- Learn from mistakes
- Track successful patterns
- Stay updated on markets

#### 3. **System Optimization**
- Monitor system performance
- Optimize resource usage
- Update configurations
- Maintain backups

---

## 📞 Support and Resources

### Getting Help
- **Email Support**: services@gocitygroup.org
- **Technical Support**: info@gocitygroup.org
- **Documentation**: Check README and API docs
- **Logs**: Review system logs for issues

### Additional Resources
- **API Documentation**: See API_DOCUMENTATION.md
- **Configuration Guide**: See CONFIGURATION.md
- **Deployment Guide**: See DEPLOYMENT.md
- **Database Schema**: See DATABASE_SCHEMA.md

### Community and Updates
- **Feature Requests**: Submit via email
- **Bug Reports**: Include logs and details
- **Updates**: Check for system updates
- **Training**: Request training sessions

---

## ⚠️ Important Disclaimers

### Trading Risks
- **Forex trading involves substantial risk**
- **Past performance does not guarantee future results**
- **Automated trading can amplify losses**
- **Always use proper risk management**

### System Limitations
- **System may not work during market gaps**
- **Technical issues can affect trading**
- **Internet connectivity required**
- **Regular monitoring recommended**

### Legal Compliance
- **Comply with local trading regulations**
- **Understand broker terms and conditions**
- **Maintain proper records**
- **Consult financial advisors if needed**

---

**Last Updated**: January 2025  
**Version**: 1.0  
**System**: G-SignalX Forex Trading Dashboard  
**Support**: services@gocitygroup.org
