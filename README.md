# Dashboard

Dashboard is an open-source application designed to assist in the creation, backtesting, and optimization of a wide variety of algorithmic trading strategies. Once refined, these strategies can be deployed as instances in live trading modes, providing a seamless transition from strategy formulation to actual trading execution.

## Features

- **Bot Orchestration**: Deploy and manage multiple instances of Hummingbot
- **Strategy Backtesting and Optimization**: Evaluate the performance of your strategies against historical data and optimize them with Optuna
- **One-Click Deployment**: Seamlessly deploy your strategies as Hummingbot instances for paper or live trading.
- **Performance Analysis Monitoring**: Monitor and analyze the performance of your deployed strategies.
- **Credential Management**: Create and manage separate accounts for API keys

## Installation

If you are a developer, and want to make changes to the code then we recommend using the Source installation below - please note that you will also need to launch the Backend API and Broker separately (through source install).   

1. **Install Dependencies**:
   - Docker Engine
   - Miniconda or Anaconda

2. **Clone Repository and Navigate to Directory**:
    ```bash
    git clone https://github.com/Justin121983/dashboard.git
    cd dashboard
    ```

3. **Create Conda Environment and Install Dependencies**:
    ```bash
    make install
    ```

4. **Activate the Isolated 'conda' Environment**:
    ```bash
    conda activate dashboard
    ```

5. **Start the Dashboard**:
    ```bash
    make run
    ```

## Authentication

Authentication is disabled by default. To enable Dashboard Authentication please follow the steps below: 

**Set Credentials (Optional):**

The dashboard uses `admin` and `abc` as the default username and password respectively. It's strongly recommended to change these credentials for enhanced security.:

- For Docker, navigate to the `deploy` folder or `dashboard` folder if using Source and open the `credentials.yml` file.
- Add or modify the current username / password and save the changes afterward
  
  ```
  credentials:
    usernames:
      admin:
        email: admin@gmail.com
        name: John Doe
        logged_in: False
        password: abc
  cookie:
    expiry_days: 0
    key: some_signature_key # Must be string
    name: some_cookie_name
  pre-authorized:
    emails:
    - admin@admin.com
  ```
  
### Source 

- Open the `CONFIG.py` file located in the dashboard root folder
- Locate the line `AUTH_SYSTEM_ENABLED = os.getenv("AUTH_SYSTEM_ENABLED", "False").lower() in ("true", "1", "t")`.
  
  ```
  CERTIFIED_EXCHANGES = ["ascendex", "binance", "bybit", "gate.io", "hitbtc", "huobi", "kucoin", "okx", "gateway"]
  CERTIFIED_STRATEGIES = ["xemm", "cross exchange market making", "pmm", "pure market making"]
  
  AUTH_SYSTEM_ENABLED = os.getenv("AUTH_SYSTEM_ENABLED", "False").lower() in ("true", "1", "t")
  
  BACKEND_API_HOST = os.getenv("BACKEND_API_HOST", "127.0.0.1")
  ```
- Change the value from `False` to `True` to enable dashboard authentication.
- Save the CONFIG.py file.
- Relaunch dashboard by running `make run`

### Known Issues
- Refreshing the browser window may log you out and display the login screen again. This is a known issue that might be addressed in future updates.
