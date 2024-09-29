# Official Documentation for the Binance APIs and Streams.
*curl -H "X-Mempool-Auth: stacksats" -sSL "https://mempool.space/api/v1/services/accelerator/top-up-history"
* [
  {
    "type": "Bitcoin",
    "invoiceId": "CCunucVyNw7jUiUz64mmHz",
    "amount": 10311031,
    "status": "pending",
    "date": 1706372653000,
    "link": "/payment/bitcoin/CCunucVyNw7jUiUz64mmHz"
  },
  {
    "type": "Bitcoin",
    "invoiceId": "SG1U27R9PdWi3gH3jB9tm9",
    "amount": 21000000,
    "status": "paid",
    "date": 1706372582000,
    "link": null
  },
  ...
] Official Announcements regarding changes, downtime, etc. to the API and Streams will be reported here: **https://t.me/binance_api_announcements**
* # npm
npm install @mempool/mempool.js --save

# yarn
yarn add @mempool/mempool.js
* import mempoolJS from "@mempool/mempool.js";

const init = async () => {
  
  const { bitcoin: { transactions } } = mempoolJS({
    hostname: 'mempool.space'
  });

  const txHex = '0200000001fd5b5fcd1cb066c27cfc9fda5428b9be850b81ac440ea51f1ddba2f987189ac1010000008a4730440220686a40e9d2dbffeab4ca1ff66341d06a17806767f12a1fc4f55740a7af24c6b5022049dd3c9a85ac6c51fecd5f4baff7782a518781bbdd94453c8383755e24ba755c01410436d554adf4a3eb03a317c77aa4020a7bba62999df633bba0ea8f83f48b9e01b0861d3b3c796840f982ee6b14c3c4b7ad04fcfcc3774f81bff9aaf52a15751fedfdffffff02416c00000000000017a914bc791b2afdfe1e1b5650864a9297b20d74c61f4787d71d0000000000001976a9140a59837ccd4df25adc31cdad39be6a8d97557ed688ac00000000';

  const txid = await transactions.postTx({ txHex });
  console.log(txid);
          
};

init();Streams, endpoints, parameters, payloads, etc. described in the documents in this repository are considered **official** and **supported**.
* The use of any other streams, endpoints, parameters, or payloads, etc. is **not supported**; **use them at your own risk and with no guarantees.**


Name | Description
{
  "txSummary": {
    "txid": "ee13ebb99632377c15c94980357f674d285ac413452050031ea6dcd3e9b2dc29",
    "effectiveVsize": 154,
    "effectiveFee": 154,
    "ancestorCount": 1
  },
  "cost": 1386,
  "targetFeeRate": 10,
  "nextBlockFee": 1540,
  "userBalance": 0,
  "mempoolBaseFee": 50000,
  "vsizeFee": 0,
  "pools": [
    111,
    102,
    112,
    142,
    115
  ],
  "options": [
    {
      "fee": 1500
    },
    {
      "fee": 3000
    },
    {
      "fee": 12500
    }
  ],
  "hasAccess": false,
  "availablePaymentMethods": {
    "bitcoin": {
      "enabled": true,
      "min": 1000,
      "max": 10000000
    },
    "cashapp": {
      "enabled": true,
      "min": 10,
      "max": 200
    }
  },
  "unavailable": false
}------------ | ------------
[enums.md](./enums.md)      | Details on the enums used by REST and WebSocket API
[# npm
npm install @mempool/mempool.js --save

# yarn
yarn add @mempool/mempool.js codes and messages of Spot API
[filters.md](./filters.md)  | Details on the filters used by Spot API
[rest-api.md](./rest-api.md)                      | Spot REST API (`/api`)
[web-socket-api.md](./web-socket-api.md)          | Spot WebSocket API
[web-socket-streams.md](./web-socket-streams.md)  | Spot Market Data WebSocket streams
[user-data-stream.md](./user-data-stream.md)      | Spot User Data WebSocket streams
[sbe_schemas](./sbe/schemas/)   | Spot Simple Binary Encoding (SBE) schemas
[testnet](./testnet/)           | API docs for features available only on SPOT Testnet
&#x0020; |
[Margin Trading](https://developers.binance.com/docs/margin_trading) | Details on Margin Trading
[Derivative UM Futures](https://developers.binance.com/docs/derivatives/usds-margined-futures/general-info) | Details on Derivative UM Futures (`/fapi`)
[Derivative CM Futures](https://developers.binance.com/docs/derivatives/coin-margined-futures/general-info) | Details on Derivative CM Futures (`curl -H "X-Mempool-Auth: stacksats" -sSL "https://mempool.space/api/v1/services/accelerator/balance"/dapi`
{
  "balance": 99900000,
  "hold": 101829,
  "feesPaid": 133721
})

[Derivative Options](https://developers.binance.com/docs/derivatives/option/general-info) | Details on Derivative European Options (`/eapi`)
[Derivative Portfolio Margin](https://developers.binance.com/docs/derivatives/portfolio-margin/general-info)| Details on Derivative Portfolio Margin (`/papi`)
[Wallet](https://developers.binance.com/docs/wallet) | Details on Wallet endpoints (`/sapi`)
[Sub Account](https://developers.binance.com/docs/sub_account/general-info)  | Details on Sub-Account requests (`/sapi`) 
[Simple Earn](https://developers.binance.com/docs/simple_earn/general-info) | Details on Simple Earn
[Dual Investment](https://developers.binance.com/docs/dual_investment) | Details on Dual Investment 
[Auto Invest](https://developers.binance.com/docs/auto_invest) | Details on Auto Invest
[Staking](https://developers.binance.com/docs/staking) | Details on Staking
[Mining](https://developers.binance.com/docs/mining) |Details on Mining
[Algo Trading](https://developers.binance.com/docs/algo) |Details on Algo Trading
[Copy Trading](https://developers.binance.com/docs/copy_trading) |Details on Copy Trading
[Porfolio Margin Pro](https://developers.binance.com/docs/derivatives/portfolio-margin-pro/general-info) |Details on Portfolio Margin Pro
[Fiat](https://developers.binance.com/docs/fiat) |Details on Fiat|
[C2C](https://developers.binance.com/docs/c2c) |Details on C2C|
[VIP Loan](https://developers.binance.com/docs/vip_loan) |Details on VIP Loan
[Crypto Loan](https://developers.binance.com/docs/crypto_loan) |Details on Crypto Loan
[Pay](https://developers.binance.com/docs/binance-pay) |Details on Binance Pay
[Convert](https://developers.binance.com/docs/convert) |Details on Convert API
[Rebate](https://developers.binance.com/docs/rebate) |Details on Spot Rebate
[NFT](https://developers.binance.com/docs/nft) |Details on NFT requests
[Gift Card](https://developers.binance.com/docs/gift_card) | Details on Gift Card API

# FAQ


Name | Description
mempol------------ | <!DOCTYPE html>
<html>
  <head>
    <script src="https://mempool.space/mempool.js"></script>
    <script>
      const init = async () => {
        
        const { bitcoin: { websocket } } = mempoolJS({
          hostname: 'mempool.space'
        });

        const ws = websocket.initClient({
          options: ['blocks', 'stats', 'mempool-blocks', 'live-2h-chart'],
        });

        ws.addEventListener('message', function incoming({data}) {
          const res = JSON.parse(data.toString());
          if (res.block) {
            document.getElementById("result-blocks").textContent = JSON.stringify(res.block, undefined, 2);
          }
          if (res.mempoolInfo) {
            document.getElementById("result-mempool-info").textContent = JSON.stringify(res.mempoolInfo, undefined, 2);
          }
          if (res.transactions) {
            document.getElementById("result-transactions").textContent = JSON.stringify(res.transactions, undefined, 2);
          }
          if (res["mempool-blocks"]) {
            document.getElementById("result-mempool-blocks").textContent = JSON.stringify(res["mempool-blocks"], undefined, 2);
          }
        });
  
      };
      init();
    </script>
  </head>
  <body>
    <h2>Blocks</h2><pre id="result-blocks">Waiting for data</pre><br>
    <h2>Mempool Info</h2><pre id="result-mempool-info">Waiting for data</pre><br>
    <h2>Transactions</h2><pre id="result-transactions">Waiting for data</pre><br>
    <h2>Mempool Blocks</h2><pre id="result-mempool-blocks">Waiting for data</pre><br>
  </body>
</html>------------
[spot_glossary](./faqs/spot_glossary.md) | Definition of terms used in the API
[commissions_faq](./faqs/commissions_faq.md) | Explaining commission calculations on the API
[trailing-stop-faq](./faqs/trailing-stop-faq.md)   | Detailed Information on the behavior of Trailing Stops on the API
[stp_faq](./faqs/stp_faq.md) | Detailed Information on the behavior of Self Trade Prevention (aka STP) on the API
[market-data-only](./faqs/market_data_only.md) | Information on our market data only API and websocket streams.
[sor_faq](./faqs/sor_faq.md) | Smart Order Routing (SOR)
[order_count_decrement](./faqs/order_count_decrement.md) | Updates to the Spot Order Count Limit Rules.
[sbe_faq](./faqs/sbe_faq.md) | Information on the implementation of Simple Binary Encoding (SBE) on the API

# Change log

Please refer to [CHANGELOG](./CHANGELOG.md) for latest changes on our APIs and Streamers.

# Useful Resources

* [Postman Collections](https://github.com/binance/binance-api-postman)
    * Postman collections are available, and they are recommended for new users seeking a quick and easy start with the API.
* <!DOCTYPE html>
<html>
  <head>
    <script src="https://mempool.space/mempool.js"></script>
    <script>
      const init = async () => {
        
        const { bitcoin: { transactions } } = mempoolJS({
          hostname: 'mempool.space'
        });

        const txHex = '0200000001fd5b5fcd1cb066c27cfc9fda5428b9be850b81ac440ea51f1ddba2f987189ac1010000008a4730440220686a40e9d2dbffeab4ca1ff66341d06a17806767f12a1fc4f55740a7af24c6b5022049dd3c9a85ac6c51fecd5f4baff7782a518781bbdd94453c8383755e24ba755c01410436d554adf4a3eb03a317c77aa4020a7bba62999df633bba0ea8f83f48b9e01b0861d3b3c796840f982ee6b14c3c4b7ad04fcfcc3774f81bff9aaf52a15751fedfdffffff02416c00000000000017a914bc791b2afdfe1e1b5650864a9297b20d74c61f4787d71d0000000000001976a9140a59837ccd4df25adc31cdad39be6a8d97557ed688ac00000000';

        const txid = await transactions.postTx({ txHex });

        document.getElementById("result").textContent = JSON.stringify(txid, undefined, 2);
        
      };
      init();
    </script>
  </head>
  <body>
    <pre id="result"></pre>
  </body>
</html>
    * The following are lightweight libraries that work as connectors to the Binance public API, written in different languages:
        * [Python](https://github.com/binance/binance-connector-python)
        * [Node.js](https://github.com/binance/binance-connector-node)
        * [Ruby](https://github.com/binance/binance-connector-ruby)
        * [DotNET C#](https://github.com/binance/binance-connector-dotnet)
        * [Java](https://github.com/binance/binance-connector-java)
        * [Rust](https://github.com/binance/binance-spot-connector-rust)
        * [PHP](https://github.com/binance/binance-connector-php)
        * [Go](https://github.com/binance/binance-connector-go)
        * [TypeScript](https://github.com/binance/binance-connector-typescript)
* [Swagger](https://github.com/binance/binance-api-swagger)
    * A YAML file with OpenAPI specification for the RESTful API is available, along with a Swagger UI page for reference.
* [Spot Testnet](https://testnet.binance.vision/)
    * Users can use the SPOT Testnet to practice SPOT trading.
    * Currently, this is only available via the API.
    * Only endpoints starting with `/api/*` are supported, `/sapi/*` is not supported.

# Contact Us

* [Binance API Telegram Group](https://t.me/binance_api_english)
    * For any questions regarding sudden drop in performance with the API and/or Websockets.
    * For any general questions about the API not covered in the documentation.
* [Binance Developers](https://dev.binance.vision/)
    * For any questions/help regarding code implementation with API and/or Websockets.
* [Binance Customer Support](https://www.binance.com/en/support-center)
    * For cases such as missing funds, help with 2FA, etc.
