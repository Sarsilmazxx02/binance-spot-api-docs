# Official Documentation for the Binance APIs and Streams.
* Official Announcements regarding changes, downtime, etc. to the API and Streams will be reported here: **https://t.me/binance_api_announcements**
* Streams, endpoints, parameters, payloads, etc. described in the documents in this repository are considered **official** and **supported**.
* The use of any other streams, endpoints, parameters, or payloads, etc. is **not supported**; **use them at your own risk and with no guarantees.**


Name | Description
------------ | ------------
[enums.md](./enums.md)      | Details on the enums used by REST and WebSocket API
[errors.md](./errors.md)    | Error codes and messages of Spot API
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
[Derivative CM Futures](https://developers.binance.com/docs/derivatives/coin-margined-futures/general-info) | Details on Derivative CM Futures (`/dapi`)
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
This XML file does not appear to have any style information associated with it. The document tree is shown below.
<sbe:messageSchema xmlns:mbx="https://binance-docs.github.io/apidocs/spot/en/" xmlns:sbe="http://fixprotocol.io/2016/sbe" xmlns:xi="http://www.w3.org/2001/XInclude" package="spot_sbe" id="1" version="0" semanticVersion="5.2" description="Spot SBE message schema" byteOrder="littleEndian">
<types>
<composite name="messageHeader" description="Template ID and length of message root">
<type name="blockLength" primitiveType="uint16"/>
<type name="templateId" primitiveType="uint16"/>
<type name="schemaId" primitiveType="uint16"/>
<type name="version" primitiveType="uint16"/>
</composite>
<composite name="groupSizeEncoding" description="Repeating group dimensions.">
<type name="blockLength" primitiveType="uint16"/>
<type name="numInGroup" primitiveType="uint32" maxValue="2147483647"/>
</composite>
<composite name="groupSize16Encoding" description="Repeating group dimensions.">
<type name="blockLength" primitiveType="uint16"/>
<type name="numInGroup" primitiveType="uint16"/>
</composite>
<composite name="varString" description="Variable length UTF-8 string.">
<type name="length" primitiveType="uint16"/>
<type name="varData" length="0" primitiveType="uint8" characterEncoding="UTF-8"/>
</composite>
<composite name="varString8" description="Variable length UTF-8 string.">
<type name="length" primitiveType="uint8"/>
<type name="varData" length="0" primitiveType="uint8" characterEncoding="UTF-8"/>
</composite>
<composite name="optionalVarString" description="Variable length UTF-8 string where an empty string means null.">
<type name="length" primitiveType="uint16"/>
<type name="varData" length="0" primitiveType="uint8" characterEncoding="UTF-8"/>
</composite>
<composite name="optionalVarString8" description="Variable length UTF-8 string where an empty string means null.">
<type name="length" primitiveType="uint8"/>
<type name="varData" length="0" primitiveType="uint8" characterEncoding="UTF-8"/>
</composite>
<composite name="messageData" description="Message header plus SBE-encoded message.">
<type name="length" primitiveType="uint32" maxValue="2147483647"/>
<type name="varData" length="0" primitiveType="uint8"/>
</composite>
<composite name="messageData16" description="Message header plus SBE-encoded message.">
<type name="length" primitiveType="uint16"/>
<type name="varData" length="0" primitiveType="uint8"/>
</composite>
<composite name="messageData8" description="Message header plus SBE-encoded message.">
<type name="length" primitiveType="uint8"/>
<type name="varData" length="0" primitiveType="uint8"/>
</composite>
<composite name="optionalMessageData" description="Message header plus SBE-encoded message where 0-length means null.">
<type name="length" primitiveType="uint32" maxValue="2147483647"/>
<type name="varData" length="0" primitiveType="uint8"/>
</composite>
<composite name="optionalMessageData16" description="Message header plus SBE-encoded message where 0-length means null.">
<type name="length" primitiveType="uint16"/>
<type name="varData" length="0" primitiveType="uint8"/>
</composite>
<type name="mantissa64" primitiveType="int64" description=" 64-bit mantissa for a decimal floating point number. The name of the field containing the exponent value is specified in the mbx:exponent attribute of the mantissa64 field. The exponent field will always precede the mantissa field."/>
<type name="mantissa128" length="16" primitiveType="uint8" description=" Signed 128-bit mantissa for a decimal floating point number represented as a little-endian byte array. The name of the field containing the exponent value is specified in the mbx:exponent attribute of the mantissa128 field. The exponent field will always precede the mantissa field. Following the convention set by the FIX SBE Standard, the value −2^127 is nullValue by default."/>
<type name="exponent8" primitiveType="int8" description=" Exponent for a decimal floating point number."/>
<type name="aggTradeId" primitiveType="int64"/>
<type name="allocId" primitiveType="int64"/>
<type name="orderId" primitiveType="int64"/>
<type name="orderListId" primitiveType="int64"/>
<type name="preventedMatchId" primitiveType="int64"/>
<type name="tradeGroupId" primitiveType="int64"/>
<type name="tradeId" primitiveType="int64"/>
<type name="updateId" primitiveType="int64"/>
<type name="utcTimestampUs" primitiveType="int64" description="UTC timestamp in microseconds"/>
<enum name="boolEnum" encodingType="uint8">
<validValue name="False">0</validValue>
<validValue name="True">1</validValue>
</enum>
<enum name="rateLimitType" encodingType="uint8">
<validValue name="RawRequests" mbx:jsonValue="RAW_REQUESTS">0</validValue>
<validValue name="Connections" mbx:jsonValue="CONNECTIONS">1</validValue>
<validValue name="RequestWeight" mbx:jsonValue="REQUEST_WEIGHT">2</validValue>
<validValue name="Orders" mbx:jsonValue="ORDERS">3</validValue>
</enum>
<enum name="rateLimitInterval" encodingType="uint8">
<validValue name="Second" mbx:jsonValue="SECOND">0</validValue>
<validValue name="Minute" mbx:jsonValue="MINUTE">1</validValue>
<validValue name="Hour" mbx:jsonValue="HOUR">2</validValue>
<validValue name="Day" mbx:jsonValue="DAY">3</validValue>
</enum>
<enum name="filterType" encodingType="uint8">
<validValue name="MaxPosition" mbx:jsonValue="MAX_POSITION">0</validValue>
<validValue name="PriceFilter" mbx:jsonValue="PRICE_FILTER">1</validValue>
<validValue name="TPlusSell" mbx:jsonValue="T_PLUS_SELL">2</validValue>
<validValue name="LotSize" mbx:jsonValue="LOT_SIZE">3</validValue>
<validValue name="MaxNumOrders" mbx:jsonValue="MAX_NUM_ORDERS">4</validValue>
<validValue name="MinNotional" mbx:jsonValue="MIN_NOTIONAL">5</validValue>
<validValue name="MaxNumAlgoOrders" mbx:jsonValue="MAX_NUM_ALGO_ORDERS">6</validValue>
<validValue name="ExchangeMaxNumOrders" mbx:jsonValue="EXCHANGE_MAX_NUM_ORDERS">7</validValue>
<validValue name="ExchangeMaxNumAlgoOrders" mbx:jsonValue="EXCHANGE_MAX_NUM_ALGO_ORDERS">8</validValue>
<validValue name="IcebergParts" mbx:jsonValue="ICEBERG_PARTS">9</validValue>
<validValue name="MarketLotSize" mbx:jsonValue="MARKET_LOT_SIZE">10</validValue>
<validValue name="PercentPrice" mbx:jsonValue="PERCENT_PRICE">11</validValue>
<validValue name="MaxNumIcebergOrders" mbx:jsonValue="MAX_NUM_ICEBERG_ORDERS">12</validValue>
<validValue name="ExchangeMaxNumIcebergOrders" mbx:jsonValue="EXCHANGE_MAX_NUM_ICEBERG_ORDERS">13</validValue>
<validValue name="TrailingDelta" mbx:jsonValue="TRAILING_DELTA">14</validValue>
<validValue name="PercentPriceBySide" mbx:jsonValue="PERCENT_PRICE_BY_SIDE">15</validValue>
<validValue name="Notional" mbx:jsonValue="NOTIONAL">16</validValue>
</enum>
<enum name="symbolStatus" encodingType="uint8">
<validValue name="PreTrading" mbx:jsonValue="PRE_TRADING">0</validValue>
<validValue name="Trading" mbx:jsonValue="TRADING">1</validValue>
<validValue name="PostTrading" mbx:jsonValue="POST_TRADING">2</validValue>
<validValue name="EndOfDay" mbx:jsonValue="END_OF_DAY">3</validValue>
<validValue name="Halt" mbx:jsonValue="HALT">4</validValue>
<validValue name="AuctionMatch" mbx:jsonValue="AUCTION_MATCH">5</validValue>
<validValue name="Break" mbx:jsonValue="BREAK">7</validValue>
</enum>
<enum name="orderType" encodingType="uint8">
<validValue name="Market" mbx:jsonValue="MARKET">0</validValue>
<validValue name="Limit" mbx:jsonValue="LIMIT">1</validValue>
<validValue name="StopLoss" mbx:jsonValue="STOP_LOSS">2</validValue>
<validValue name="StopLossLimit" mbx:jsonValue="STOP_LOSS_LIMIT">3</validValue>
<validValue name="TakeProfit" mbx:jsonValue="TAKE_PROFIT">4</validValue>
<validValue name="TakeProfitLimit" mbx:jsonValue="TAKE_PROFIT_LIMIT">5</validValue>
<validValue name="LimitMaker" mbx:jsonValue="LIMIT_MAKER">6</validValue>
</enum>
<set name="orderTypes" encodingType="uint16">
<choice name="Market" mbx:jsonValue="MARKET">0</choice>
<choice name="Limit" mbx:jsonValue="LIMIT">1</choice>
<choice name="StopLoss" mbx:jsonValue="STOP_LOSS">2</choice>
<choice name="StopLossLimit" mbx:jsonValue="STOP_LOSS_LIMIT">3</choice>
<choice name="TakeProfit" mbx:jsonValue="TAKE_PROFIT">4</choice>
<choice name="TakeProfitLimit" mbx:jsonValue="TAKE_PROFIT_LIMIT">5</choice>
<choice name="LimitMaker" mbx:jsonValue="LIMIT_MAKER">6</choice>
</set>
<enum name="selfTradePreventionMode" encodingType="uint8">
<validValue name="None" mbx:jsonValue="NONE">1</validValue>
<validValue name="ExpireTaker" mbx:jsonValue="EXPIRE_TAKER">2</validValue>
<validValue name="ExpireMaker" mbx:jsonValue="EXPIRE_MAKER">3</validValue>
<validValue name="ExpireBoth" mbx:jsonValue="EXPIRE_BOTH">4</validValue>
</enum>
<enum name="allocationType" encodingType="uint8">
<validValue name="Unknown" mbx:jsonValue="UNKNOWN">0</validValue>
<validValue name="Sor" mbx:jsonValue="SOR">2</validValue>
</enum>
<enum name="accountType" encodingType="uint8">
<validValue name="Spot" mbx:jsonValue="SPOT">0</validValue>
<validValue name="Unknown" mbx:jsonValue="UNKNOWN">2</validValue>
</enum>
<set name="allowedSelfTradePreventionModes" encodingType="uint8">
<choice name="None" mbx:jsonValue="NONE">0</choice>
<choice name="ExpireTaker" mbx:jsonValue="EXPIRE_TAKER">1</choice>
<choice name="ExpireMaker" mbx:jsonValue="EXPIRE_MAKER">2</choice>
<choice name="ExpireBoth" mbx:jsonValue="EXPIRE_BOTH">3</choice>
</set>
<enum name="orderStatus" encodingType="uint8">
<validValue name="New" mbx:jsonValue="NEW">0</validValue>
<validValue name="PartiallyFilled" mbx:jsonValue="PARTIALLY_FILLED">1</validValue>
<validValue name="Filled" mbx:jsonValue="FILLED">2</validValue>
<validValue name="Canceled" mbx:jsonValue="CANCELED">3</validValue>
<validValue name="PendingCancel" mbx:jsonValue="PENDING_CANCEL">4</validValue>
<validValue name="Rejected" mbx:jsonValue="REJECTED">5</validValue>
<validValue name="Expired" mbx:jsonValue="EXPIRED">6</validValue>
<validValue name="ExpiredInMatch" mbx:jsonValue="EXPIRED_IN_MATCH">9</validValue>
<validValue name="Unknown" mbx:jsonValue="UNKNOWN">254</validValue>
</enum>
<enum name="orderSide" encodingType="uint8">
<validValue name="Buy" mbx:jsonValue="BUY">0</validValue>
<validValue name="Sell" mbx:jsonValue="SELL">1</validValue>
</enum>
<enum name="orderCapacity" encodingType="uint8">
<validValue name="Principal" mbx:jsonValue="PRINCIPAL">1</validValue>
<validValue name="Agency" mbx:jsonValue="AGENCY">2</validValue>
</enum>
<enum name="timeInForce" encodingType="uint8">
<validValue name="Gtc" mbx:jsonValue="GTC">0</validValue>
<validValue name="Ioc" mbx:jsonValue="IOC">1</validValue>
<validValue name="Fok" mbx:jsonValue="FOK">2</validValue>
</enum>
<enum name="floor" encodingType="uint8">
<validValue name="Exchange" mbx:jsonValue="EXCHANGE">1</validValue>
<validValue name="Broker" mbx:jsonValue="BROKER">2</validValue>
<validValue name="Sor" mbx:jsonValue="SOR">3</validValue>
</enum>
<enum name="matchType" encodingType="uint8">
<validValue name="AutoMatch" mbx:jsonValue="AUTO_MATCH">1</validValue>
<validValue name="OnePartyTradeReport" mbx:jsonValue="ONE_PARTY_TRADE_REPORT">2</validValue>
</enum>
<enum name="contingencyType" encodingType="uint8">
<validValue name="Oco" mbx:jsonValue="OCO">1</validValue>
</enum>
<enum name="listStatusType" encodingType="uint8">
<validValue name="Response" mbx:jsonValue="RESPONSE">0</validValue>
<validValue name="ExecStarted" mbx:jsonValue="EXEC_STARTED">1</validValue>
<validValue name="AllDone" mbx:jsonValue="ALL_DONE">2</validValue>
</enum>
<enum name="listOrderStatus" encodingType="uint8">
<validValue name="Canceling" mbx:jsonValue="CANCELING">0</validValue>
<validValue name="Executing" mbx:jsonValue="EXECUTING">1</validValue>
<validValue name="AllDone" mbx:jsonValue="ALL_DONE">2</validValue>
<validValue name="Reject" mbx:jsonValue="REJECT">3</validValue>
</enum>
<enum name="cancelReplaceStatus" encodingType="uint8">
<validValue name="Success" mbx:jsonValue="SUCCESS">0</validValue>
<validValue name="Failure" mbx:jsonValue="FAILURE">1</validValue>
<validValue name="NotAttempted" mbx:jsonValue="NOT_ATTEMPTED">2</validValue>
</enum>
</types>
<sbe:message name="PriceFilter" id="1">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.PriceFilter"/>
<field id="2" name="priceExponent" type="exponent8"/>
<field id="3" name="minPrice" type="mantissa64" mbx:exponent="priceExponent"/>
<field id="4" name="maxPrice" type="mantissa64" mbx:exponent="priceExponent"/>
<field id="5" name="tickSize" type="mantissa64" mbx:exponent="priceExponent"/>
</sbe:message>
<sbe:message name="PercentPriceFilter" id="2">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.PercentPrice"/>
<field id="2" name="multiplierExponent" type="exponent8"/>
<field id="3" name="multiplierUp" type="mantissa64" mbx:exponent="multiplierExponent"/>
<field id="4" name="multiplierDown" type="mantissa64" mbx:exponent="multiplierExponent"/>
<field id="5" name="avgPriceMins" type="int32"/>
</sbe:message>
<sbe:message name="PercentPriceBySideFilter" id="3">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.PercentPriceBySide"/>
<field id="2" name="multiplierExponent" type="exponent8"/>
<field id="3" name="bidMultiplierUp" type="mantissa64" mbx:exponent="multiplierExponent"/>
<field id="4" name="bidMultiplierDown" type="mantissa64" mbx:exponent="multiplierExponent"/>
<field id="5" name="askMultiplierUp" type="mantissa64" mbx:exponent="multiplierExponent"/>
<field id="6" name="askMultiplierDown" type="mantissa64" mbx:exponent="multiplierExponent"/>
<field id="7" name="avgPriceMins" type="int32"/>
</sbe:message>
<sbe:message name="LotSizeFilter" id="4">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.LotSize"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="minQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="4" name="maxQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="5" name="stepSize" type="mantissa64" mbx:exponent="qtyExponent"/>
</sbe:message>
<sbe:message name="MinNotionalFilter" id="5">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.MinNotional"/>
<field id="2" name="priceExponent" type="exponent8"/>
<field id="3" name="minNotional" type="mantissa64" mbx:exponent="priceExponent"/>
<field id="4" name="applyToMarket" type="boolEnum"/>
<field id="5" name="avgPriceMins" type="int32"/>
</sbe:message>
<sbe:message name="NotionalFilter" id="6">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.Notional"/>
<field id="2" name="priceExponent" type="exponent8"/>
<field id="3" name="minNotional" type="mantissa64" mbx:exponent="priceExponent"/>
<field id="4" name="applyMinToMarket" type="boolEnum"/>
<field id="5" name="maxNotional" type="mantissa64" mbx:exponent="priceExponent"/>
<field id="6" name="applyMaxToMarket" type="boolEnum"/>
<field id="7" name="avgPriceMins" type="int32"/>
</sbe:message>
<sbe:message name="IcebergPartsFilter" id="7">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.IcebergParts"/>
<field id="2" name="filterLimit" type="int64" mbx:jsonPath="limit"/>
</sbe:message>
<sbe:message name="MarketLotSizeFilter" id="8">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.MarketLotSize"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="minQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="4" name="maxQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="5" name="stepSize" type="mantissa64" mbx:exponent="qtyExponent"/>
</sbe:message>
<sbe:message name="MaxNumOrdersFilter" id="9">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.MaxNumOrders"/>
<field id="2" name="maxNumOrders" type="int64"/>
</sbe:message>
<sbe:message name="MaxNumAlgoOrdersFilter" id="10">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.MaxNumAlgoOrders"/>
<field id="2" name="maxNumAlgoOrders" type="int64"/>
</sbe:message>
<sbe:message name="MaxNumIcebergOrdersFilter" id="11">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.MaxNumIcebergOrders"/>
<field id="2" name="maxNumIcebergOrders" type="int64"/>
</sbe:message>
<sbe:message name="MaxPositionFilter" id="12">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.MaxPosition"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="maxPosition" type="mantissa64" mbx:exponent="qtyExponent"/>
</sbe:message>
<sbe:message name="TrailingDeltaFilter" id="13">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.TrailingDelta"/>
<field id="2" name="minTrailingAboveDelta" type="int64"/>
<field id="3" name="maxTrailingAboveDelta" type="int64"/>
<field id="4" name="minTrailingBelowDelta" type="int64"/>
<field id="5" name="maxTrailingBelowDelta" type="int64"/>
</sbe:message>
<sbe:message name="TPlusSellFilter" id="14">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.TPlusSell"/>
<field id="2" name="endTime" type="utcTimestampUs" presence="optional"/>
</sbe:message>
<sbe:message name="ExchangeMaxNumOrdersFilter" id="15">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.ExchangeMaxNumOrders"/>
<field id="2" name="maxNumOrders" type="int64"/>
</sbe:message>
<sbe:message name="ExchangeMaxNumAlgoOrdersFilter" id="16">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.ExchangeMaxNumAlgoOrders"/>
<field id="2" name="maxNumAlgoOrders" type="int64"/>
</sbe:message>
<sbe:message name="ExchangeMaxNumIcebergOrdersFilter" id="17">
<field id="1" name="filterType" type="filterType" presence="constant" valueRef="filterType.ExchangeMaxNumIcebergOrders"/>
<field id="2" name="maxNumIcebergOrders" type="int64"/>
</sbe:message>
<!--  Endpoint responses begin here  -->
<sbe:message name="WebSocketResponse" id="50" description="Message wrapper for WebSocket API.">
<field id="1" name="sbeSchemaIdVersionDeprecated" type="boolEnum"/>
<field id="2" name="status" type="uint16"/>
<group id="100" name="rateLimits" dimensionType="groupSize16Encoding">
<field id="1" name="rateLimitType" type="rateLimitType"/>
<field id="2" name="interval" type="rateLimitInterval"/>
<field id="3" name="intervalNum" type="uint8"/>
<field id="4" name="rateLimit" type="int64" mbx:jsonPath="limit"/>
<field id="5" name="current" type="int64" mbx:jsonPath="count"/>
</group>
<!--  While the request parameter "id" may be an integer, string or
            null, the response field "id" is always a string. Integers are
            converted to strings and null is converted to the empty string.  -->
<data id="200" name="id" type="varString8"/>
<!--  Contains one of the <sbe:message/> types that follow.
            Use the "templateId" field from the "messageHeader" to
            differentiate them. When using WebSocket API, even
            "ErrorResponse" is wrapped by "WebSocketResponse".  -->
<data id="201" name="result" type="messageData"/>
</sbe:message>
<!--  Response for WebSocket "method":"session.logon"  -->
<sbe:message name="WebSocketSessionLogonResponse" id="51">
<field id="1" name="authorizedSince" type="utcTimestampUs"/>
<field id="2" name="connectedSince" type="utcTimestampUs"/>
<field id="3" name="returnRateLimits" type="boolEnum"/>
<field id="4" name="serverTime" type="utcTimestampUs"/>
<data id="200" name="apiKey" type="varString"/>
</sbe:message>
<!--  Response for WebSocket "method":"session.status"  -->
<sbe:message name="WebSocketSessionStatusResponse" id="52">
<field id="1" name="authorizedSince" type="utcTimestampUs" presence="optional"/>
<field id="2" name="connectedSince" type="utcTimestampUs"/>
<field id="3" name="returnRateLimits" type="boolEnum"/>
<field id="4" name="serverTime" type="utcTimestampUs"/>
<data id="200" name="apiKey" type="optionalVarString"/>
</sbe:message>
<!--  Response for WebSocket "method":"session.logout"  -->
<sbe:message name="WebSocketSessionLogoutResponse" id="53">
<field id="1" name="authorizedSince" type="utcTimestampUs" presence="optional"/>
<field id="2" name="connectedSince" type="utcTimestampUs"/>
<field id="3" name="returnRateLimits" type="boolEnum"/>
<field id="4" name="serverTime" type="utcTimestampUs"/>
<data id="200" name="apiKey" type="optionalVarString"/>
</sbe:message>
<sbe:message name="ErrorResponse" id="100">
<field id="1" name="code" type="int16"/>
<field id="2" name="serverTime" type="utcTimestampUs" presence="optional"/>
<field id="3" name="retryAfter" type="utcTimestampUs" presence="optional"/>
<data id="200" name="msg" type="varString"/>
<!--  May contain a "CancelReplaceOrderResponse" message  -->
<data id="201" name="data" type="optionalMessageData"/>
</sbe:message>
<!--  General endpoints  -->
<!--  Response for
        - REST GET /api/v3/ping
        - WebSocket "method":"ping"  -->
<sbe:message name="PingResponse" id="101"> </sbe:message>
<!--  Response for
        - REST GET /api/v3/time
        - WebSocket "method":"time"  -->
<sbe:message name="ServerTimeResponse" id="102">
<field id="1" name="serverTime" type="utcTimestampUs"/>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/exchangeInfo
        - WebSocket "method":"exchangeInfo"  -->
<sbe:message name="ExchangeInfoResponse" id="103">
<!--  "timeZone" in JSON response is omitted. All timestamps in SBE
            responses are in UTC.  -->
<!--  "serverTime" in JSON response is omitted. See GET /api/v3/time  -->
<group id="100" name="rateLimits">
<field id="1" name="rateLimitType" type="rateLimitType"/>
<field id="2" name="interval" type="rateLimitInterval"/>
<field id="3" name="intervalNum" type="uint8"/>
<field id="4" name="rateLimit" type="int64" mbx:jsonPath="limit"/>
</group>
<group id="101" name="exchangeFilters">
<!--  Contains one of
                - "ExchangeMaxNumOrdersFilter"
                - "ExchangeMaxNumAlgoOrdersFilter"
                - "ExchangeMaxNumIcebergOrdersFilter"
                Use the "templateId" field from the "messageHeader" to
                differentiate them.  -->
<data id="200" name="filter" type="messageData8" mbx:jsonPath=".."/>
</group>
<group id="102" name="symbols">
<field id="1" name="status" type="symbolStatus"/>
<field id="2" name="baseAssetPrecision" type="uint8"/>
<field id="3" name="quoteAssetPrecision" type="uint8"/>
<field id="4" name="baseCommissionPrecision" type="uint8"/>
<field id="5" name="quoteCommissionPrecision" type="uint8"/>
<field id="6" name="orderTypes" type="orderTypes"/>
<field id="7" name="icebergAllowed" type="boolEnum"/>
<field id="8" name="ocoAllowed" type="boolEnum"/>
<field id="9" name="quoteOrderQtyMarketAllowed" type="boolEnum"/>
<field id="10" name="allowTrailingStop" type="boolEnum"/>
<field id="11" name="cancelReplaceAllowed" type="boolEnum"/>
<field id="12" name="isSpotTradingAllowed" type="boolEnum"/>
<field id="13" name="isMarginTradingAllowed" type="boolEnum"/>
<field id="14" name="defaultSelfTradePreventionMode" type="selfTradePreventionMode"/>
<field id="15" name="allowedSelfTradePreventionModes" type="allowedSelfTradePreventionModes"/>
<group id="100" name="filters">
<!--  Contains one of
                    - "PriceFilter"
                    - "PercentPriceFilter"
                    - "PercentPriceBySideFilter"
                    - "LotSizeFilter"
                    - "MinNotionalFilter"
                    - "NotionalFilter"
                    - "IcebergPartsFilter"
                    - "MarketLotSizeFilter"
                    - "MaxNumOrdersFilter"
                    - "MaxNumAlgoOrdersFilter"
                    - "MaxNumIcebergOrdersFilter"
                    - "MaxPositionFilter"
                    - "TrailingDeltaFilter"
                    - "TPlusSellFilter"
                    Use the "templateId" field from the "messageHeader" to
                    differentiate them.  -->
<data id="200" name="filter" type="messageData8" mbx:jsonPath=".."/>
</group>
<group id="101" name="permissions">
<data id="200" name="permission" type="varString8" mbx:jsonPath=".."/>
</group>
<data id="200" name="symbol" type="varString8"/>
<data id="201" name="baseAsset" type="varString8"/>
<data id="202" name="quoteAsset" type="varString8"/>
</group>
<group id="103" name="sors">
<group id="1" name="sorSymbols">
<data id="200" name="symbol" type="varString8" mbx:jsonPath=".."/>
</group>
<data id="200" name="baseAsset" type="varString8"/>
</group>
</sbe:message>
<!--  Market data endpoint  -->
<!--  Response for
        - REST GET /api/v3/depth
        - WebSocket "method":"depth"  -->
<sbe:message name="DepthResponse" id="200">
<field id="1" name="lastUpdateId" type="updateId"/>
<field id="2" name="priceExponent" type="exponent8"/>
<field id="3" name="qtyExponent" type="exponent8"/>
<group id="100" name="bids">
<field id="1" name="price" type="mantissa64" mbx:exponent="priceExponent" mbx:jsonPath="[]"/>
<field id="2" name="qty" type="mantissa64" mbx:exponent="qtyExponent" mbx:jsonPath="[]"/>
</group>
<group id="101" name="asks">
<field id="1" name="price" type="mantissa64" mbx:exponent="priceExponent" mbx:jsonPath="[]"/>
<field id="2" name="qty" type="mantissa64" mbx:exponent="qtyExponent" mbx:jsonPath="[]"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/trades
        - REST GET /api/v3/historicalTrades
        - WebSocket "method":"trades.recent"
        - WebSocket "method":"trades.historical"  -->
<sbe:message name="TradesResponse" id="201">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<group id="100" name="trades" mbx:jsonPath="..">
<field id="1" name="id" type="tradeId"/>
<field id="2" name="price" type="mantissa64" mbx:exponent="priceExponent"/>
<field id="3" name="qty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="4" name="quoteQty" type="mantissa64" mbx:exponent="priceExponent"/>
<field id="5" name="time" type="utcTimestampUs"/>
<field id="6" name="isBuyerMaker" type="boolEnum"/>
<field id="7" name="isBestMatch" type="boolEnum"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/aggTrades
        - WebSocket "method":"trades.aggregate"  -->
<sbe:message name="AggTradesResponse" id="202">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<group id="100" name="aggTrades" mbx:jsonPath="..">
<field id="1" name="aggTradeId" type="aggTradeId"/>
<field id="2" name="price" type="mantissa64" mbx:exponent="priceExponent"/>
<field id="3" name="qty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="4" name="firstTradeId" type="tradeId"/>
<field id="5" name="lastTradeId" type="tradeId"/>
<field id="7" name="time" type="utcTimestampUs"/>
<field id="8" name="isBuyerMaker" type="boolEnum"/>
<field id="9" name="isBestMatch" type="boolEnum"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/klines
        - REST GET /api/v3/uiKlines
        - WebSocket "method":"klines"
        - WebSocket "method":"uiKlines"  -->
<sbe:message name="KlinesResponse" id="203">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<group id="100" name="klines" mbx:jsonPath="..">
<field id="1" name="openTime" type="utcTimestampUs" mbx:jsonPath="[]"/>
<field id="2" name="openPrice" type="mantissa64" mbx:exponent="priceExponent" mbx:jsonPath="[]"/>
<field id="3" name="highPrice" type="mantissa64" mbx:exponent="priceExponent" mbx:jsonPath="[]"/>
<field id="4" name="lowPrice" type="mantissa64" mbx:exponent="priceExponent" mbx:jsonPath="[]"/>
<field id="5" name="closePrice" type="mantissa64" mbx:exponent="priceExponent" mbx:jsonPath="[]"/>
<field id="6" name="volume" type="mantissa128" mbx:exponent="qtyExponent" mbx:jsonPath="[]"/>
<field id="7" name="closeTime" type="utcTimestampUs" mbx:jsonPath="[]"/>
<field id="8" name="quoteVolume" type="mantissa128" mbx:exponent="priceExponent" mbx:jsonPath="[]"/>
<field id="9" name="numTrades" type="int64" mbx:jsonPath="[]"/>
<field id="10" name="takerBuyBaseVolume" type="mantissa128" mbx:exponent="qtyExponent" mbx:jsonPath="[]"/>
<field id="11" name="takerBuyQuoteVolume" type="mantissa128" mbx:exponent="priceExponent" mbx:jsonPath="[]"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/avgPrice
        - WebSocket "method":"avgPrice"  -->
<sbe:message name="AveragePriceResponse" id="204">
<field id="1" name="mins" type="int64"/>
<field id="2" name="priceExponent" type="exponent8"/>
<field id="3" name="price" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="closeTime" type="utcTimestampUs" presence="optional"/>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker/24hr?symbol=SYMBOL&type=FULL
        - WebSocket "method":"ticker.24hr","params":{"symbol":"<SYMBOL>","type":"FULL"}  -->
<sbe:message name="Ticker24hSymbolFullResponse" id="205">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="priceChange" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="priceChangePercent" type="float" presence="optional"/>
<field id="5" name="weightedAvgPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="6" name="prevClosePrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="7" name="lastPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="8" name="lastQty" type="mantissa128" mbx:exponent="qtyExponent"/>
<field id="9" name="bidPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="10" name="bidQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="11" name="askPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="12" name="askQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="13" name="openPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="14" name="highPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="15" name="lowPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="16" name="volume" type="mantissa128" mbx:exponent="qtyExponent"/>
<field id="17" name="quoteVolume" type="mantissa128" mbx:exponent="priceExponent"/>
<field id="18" name="openTime" type="utcTimestampUs"/>
<field id="19" name="closeTime" type="utcTimestampUs"/>
<field id="20" name="firstId" type="tradeId" presence="optional"/>
<field id="21" name="lastId" type="tradeId" presence="optional"/>
<field id="22" name="numTrades" type="int64" mbx:jsonPath="count"/>
<data id="200" name="symbol" type="varString8"/>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker/24hr?type=FULL
        - WebSocket "method":"ticker.24hr","params":{"type":"FULL"}  -->
<sbe:message name="Ticker24hFullResponse" id="206">
<group id="100" name="tickers" mbx:jsonPath="..">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="priceChange" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="priceChangePercent" type="float" presence="optional"/>
<field id="5" name="weightedAvgPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="6" name="prevClosePrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="7" name="lastPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="8" name="lastQty" type="mantissa128" mbx:exponent="qtyExponent"/>
<field id="9" name="bidPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="10" name="bidQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="11" name="askPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="12" name="askQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="13" name="openPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="14" name="highPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="15" name="lowPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="16" name="volume" type="mantissa128" mbx:exponent="qtyExponent"/>
<field id="17" name="quoteVolume" type="mantissa128" mbx:exponent="priceExponent"/>
<field id="18" name="openTime" type="utcTimestampUs"/>
<field id="19" name="closeTime" type="utcTimestampUs"/>
<field id="20" name="firstId" type="tradeId" presence="optional"/>
<field id="21" name="lastId" type="tradeId" presence="optional"/>
<field id="22" name="numTrades" type="int64" mbx:jsonPath="count"/>
<data id="200" name="symbol" type="varString8"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker/24hr?symbol=SYMBOL&type=MINI
        - WebSocket "method":"ticker.24hr","params":{"symbol":"<SYMBOL>","type":"MINI"}  -->
<sbe:message name="Ticker24hSymbolMiniResponse" id="207">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="openPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="highPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="5" name="lowPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="6" name="lastPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="7" name="volume" type="mantissa128" mbx:exponent="qtyExponent"/>
<field id="8" name="quoteVolume" type="mantissa128" mbx:exponent="priceExponent"/>
<field id="9" name="openTime" type="utcTimestampUs"/>
<field id="10" name="closeTime" type="utcTimestampUs"/>
<field id="11" name="firstId" type="tradeId" presence="optional"/>
<field id="12" name="lastId" type="tradeId" presence="optional"/>
<field id="13" name="numTrades" type="int64" mbx:jsonPath="count"/>
<data id="200" name="symbol" type="varString8"/>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker/24hr?type=MINI
        - WebSocket "method":"ticker.24hr","params":{"type":"MINI"}  -->
<sbe:message name="Ticker24hMiniResponse" id="208">
<group id="100" name="tickers" mbx:jsonPath="..">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="openPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="highPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="5" name="lowPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="6" name="lastPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="7" name="volume" type="mantissa128" mbx:exponent="qtyExponent"/>
<field id="8" name="quoteVolume" type="mantissa128" mbx:exponent="priceExponent"/>
<field id="9" name="openTime" type="utcTimestampUs"/>
<field id="10" name="closeTime" type="utcTimestampUs"/>
<field id="11" name="firstId" type="tradeId" presence="optional"/>
<field id="12" name="lastId" type="tradeId" presence="optional"/>
<field id="13" name="numTrades" type="int64" mbx:jsonPath="count"/>
<data id="200" name="symbol" type="varString8"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker/price?symbol=
        - WebSocket "method":"ticker.price","params":{"symbol":"<SYMBOL>"}  -->
<sbe:message name="PriceTickerSymbolResponse" id="209">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="price" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<data id="200" name="symbol" type="varString8"/>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker/price?symbols=
        - Websocket "method":"ticker.price","params":{"symbols":[<SYMBOLS>]}  -->
<sbe:message name="PriceTickerResponse" id="210">
<group id="100" name="tickers" mbx:jsonPath="..">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="price" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<data id="200" name="symbol" type="varString8"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker/bookTicker?symbol=
        - WebSocket "method":"ticker.book","params":{"symbol":"<SYMBOL>"}  -->
<sbe:message name="BookTickerSymbolResponse" id="211">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="bidPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="bidQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="5" name="askPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="6" name="askQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<data id="200" name="symbol" type="varString8"/>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker/bookTicker?symbols=
        - WebSocket "method":"ticker.book","params":{"symbols":[<SYMBOLS>]}  -->
<sbe:message name="BookTickerResponse" id="212">
<group id="100" name="tickers" mbx:jsonPath="..">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="bidPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="bidQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<field id="5" name="askPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="6" name="askQty" type="mantissa64" mbx:exponent="qtyExponent"/>
<data id="200" name="symbol" type="varString8"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker?symbol=SYMBOL&type=FULL
        - REST GET /api/v3/tradingDay?symbol=SYMBOL&type=FULL
        - WebSocket "method":"ticker","params":{"symbol":"<SYMBOL>","type":"FULL"}
        - WebSocket "method":"ticker.tradingDay","params":{"symbol":"<SYMBOL>","type":"FULL"}  -->
<sbe:message name="TickerSymbolFullResponse" id="213">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="priceChange" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="priceChangePercent" type="float" presence="optional"/>
<field id="5" name="weightedAvgPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="6" name="openPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="7" name="highPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="8" name="lowPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="9" name="lastPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="10" name="volume" type="mantissa128" mbx:exponent="qtyExponent"/>
<field id="11" name="quoteVolume" type="mantissa128" mbx:exponent="priceExponent"/>
<field id="12" name="openTime" type="utcTimestampUs"/>
<field id="13" name="closeTime" type="utcTimestampUs"/>
<field id="14" name="firstId" type="tradeId" presence="optional"/>
<field id="15" name="lastId" type="tradeId" presence="optional"/>
<field id="16" name="numTrades" type="int64" mbx:jsonPath="count"/>
<data id="200" name="symbol" type="varString8"/>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker?type=FULL&symbols=
        - REST GET /api/v3/tradingDay?type=FULL&symbols=
        - WebSocket "method":"ticker","params":{"type":"FULL","symbols":[<SYMBOLS>]}
        - WebSocket "method":"ticker.tradingDay","params":{"type":"FULL","symbols":[<SYMBOLS>]}  -->
<sbe:message name="TickerFullResponse" id="214">
<group id="100" name="tickers" mbx:jsonPath="..">
<field id="1" name="priceExponent" type="exponent8"/>
<field id="2" name="qtyExponent" type="exponent8"/>
<field id="3" name="priceChange" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="4" name="priceChangePercent" type="float" presence="optional"/>
<field id="5" name="weightedAvgPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="6" name="openPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="7" name="highPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="8" name="lowPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="9" name="lastPrice" type="mantissa64" mbx:exponent="priceExponent" presence="optional"/>
<field id="10" name="volume" type="mantissa128" mbx:exponent="qtyExponent"/>
<field id="11" name="quoteVolume" type="mantissa128" mbx:exponent="priceExponent"/>
<field id="12" name="openTime" type="utcTimestampUs"/>
<field id="13" name="closeTime" type="utcTimestampUs"/>
<field id="14" name="firstId" type="tradeId" presence="optional"/>
<field id="15" name="lastId" type="tradeId" presence="optional"/>
<field id="16" name="numTrades" type="int64" mbx:jsonPath="count"/>
<data id="200" name="symbol" type="varString8"/>
</group>
</sbe:message>
<!--  Response for
        - REST GET /api/v3/ticker?symbol=SYMBOL&type=MINI
        - REST GET /api/v3/tradingDay?symbol=SYMBOL&type=MINI
        - WebSocket "method":"ticker","params":{"symbol":"<SYMBOL>","type":"MINI"]}
        - WebSocket "method":"ticker.tradingDay","params":{"symbol":"<SYMBOL>","type":"MINI"}  -->
<sbe:message
[Pay](https://developers.binance.com/docs/binance-pay) |Details on Binance Pay
[Convert](https://developers.binance.com/docs/convert) |Details on Convert API
[Rebate](https://developers.binance.com/docs/rebate) |Details on Spot Rebate
[NFT](https://developers.binance.com/docs/nft) |Details on NFT requests
[Gift Card](https://developers.binance.com/docs/gift_card) | Details on Gift Card API

# FAQ


Name | Description
------------ | ------------
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
* Connectors
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
