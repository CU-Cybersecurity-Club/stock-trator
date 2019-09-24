Unnamed Stock Trading Wargame
=============================

This doc lays out the rough design details of a yet-unnamed wargame based around a stock trading site. Why focus the game on stock trading?
- Realistic enough that it could be an actual product.
- Provides clear stakes through the ability to gain or lose "money" through hacks.
- Allows a real-time leaderboard in the form of particpents' balances.
- Able to be played by many people at the same time.
- Allows students with weaker technical skills to still participate through regular play, if they get lost or bored.
  
The game would support, at a minimum, these features:
- A real-time list of stocks with prices that fluctuate based on a simple supply/demand model.
- A leaderboard - in this case a public list of users and their cash/stock balances.
- User accounts.
   - Participents can create 'inventment accounts' that start with a small amount of money, and can buy and sell stock options to make more.
- Bot accounts that users can exploit.
   - These accounts would start with large cash balances that could be 'stolen' to that users target them instead of each other.
   - These bots would trade in randomish patterns, to keep prices fluctuating.

Some vulnerabilities that could be exploited:
- No CSRF tokens could allow attackers to buy/sell stock on behalf of others.
- Poor passwords on bot accounts could allow them to be brute-forced and taken over.
- XSS in URL parameters could be used to buy/sell stock on behalf of others.
- Client-side verification of basic checks (i.e. liquid cash is above zero) can be bypassed to perform illigal transactions.
- Length extension attack on URL params when buying or selling stock.
  - Would require some reason to allow multiple transactions in one request, which would be an extra feature but makes sense for stock trading.
- Anything else we think of.