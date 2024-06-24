## Data Dictionary

Swaps Pool 0 (raw data)<br>

- p0.transaction_time (string) - Timestamp for Pool 0 transaction.<br>
- p0.transaciton_epoch_time (long)  - Epoch Time for Pool 0 transaction.<br>
- p0.t0_amount (float) - Token 0 (USDC) transaction amount for Pool 0.  THis can be negative if its removing money from the pool (sell), positive if adding money (buy).<br>
- p0.t1_amount (float) - Token 1 (ETH) transaction amount for Pool 0.  THis can be negative if its removing money from the pool (sell), positive if adding money (buy).<br>
- p0.t0_token (string) - Token 0 (USDC) address for Pool 0(this can be used to find out more information about the token on the ethereum network).<br>
- p0.t1_token (string) - Token 1 (ETH) address for Pool 0(this can be used to find out more information about the token on the ethereum network).<br>
- p0.tick (long) - Ethereum Transaction Tick for Pool 0 - This is used as a proxy for price of ETH .  It is often used to regulate when prices will change in a pool.<br>
- p0.sqrtPriceX96 (long) - Ethereum Square Root Price for Pool 0 (long) - used to derive the price of ETH.  This is a high resolution version of the tick.  The sqrtPriceX96 conversion equation is [here](https://blog.uniswap.org/uniswap-v3-math-primer) <br>
- p0.gasUsed (long) - this is a integer number of units of work used to process the transaction in Pool 0.  THis combined with price gives you the gas fees.  <br>
- p0.gasPrice (long) - this is a price of each unit of work used to process the transaction in Pool 0.<br>
- p0.blockNumber (long) - this is a hash used to identify the block where the transaction is validated in Pool 0.<br>
- p0.sender (string) - hash of the sender (buyer) in Pool 0 for the specific transaction.<br>
- p0.recipient (string) - hash of the recipient (seller) in Pool 0 for the specific transaction. <br>
- p0.transaction_id (string) - hash id for the transaction in Pool 0. <br>

Swaps Pool 0 (calculated)<br>
- p0.transaction_rate (float) - pool 0 transaction rate (fixed for all transactions)<br>
- p0.transaction_fee_usd (float) - transaction fee in USDC.  p0.transaction_rate * p0.t1_amount<br>
- p0.gas_fees_usd - total gas fees for Pool 0 calculated from gasUsed*gasPrice.<br>
- p0.total_fees_usd - sum of p0.gas_fees_usd and p0.transaction_fee_usd.<br>
- p0.eth_price_usd - conversion from sqrtPriceX96 to USDC per ETH.<br>

Swaps Pool 1 (raw data)<br>
- same as above

Swaps Pool 1 (calculated)<br>
- same as above

Both Pools<br>
- percent_change - Percent Change in price betwen Pool 0 and Pool 1.  (p0.eth_price_usd-p1.eth_price_usd)/min(p1.eth_price_usd,p0.eth_price_usd)<br>
- total_gas_fees_usd - sum of total gas fees from both Pool 0 and Pool 1.<br>
- total_transaction_rate - sum of transaction rates (not price) from both Pool 0 and Pool 1.  p0.transaction_rate + p1.transaction_rate
- total_fees_usd - sum of total_gas_fees_usd and total_transaction_fees_usd<br>
- total_transaction_fees_usd - sum of all transaction fees in Pool 0 and Pool 1.  p0.transaction_fee_usd and p1.transaction_fee_usd<br>
- swap_go_nogo (1 or 0) - Metric to determine if arbitrage exists immediately after a transaction.  1 if total_gas_fees_usd / (|percent_change| - total_transaction_rate) > 0 <br>

Google Trends<br>
- bitcoin_trend<br>
- crypto_currency_trend<br>
- ethereum_trend<br>
- USDC_trend<br>
- WETH_trend<br>

Global Hourly Price of Ethereum (fetched from thegraph.com)<br>
- global_eth_price_usd<br>
