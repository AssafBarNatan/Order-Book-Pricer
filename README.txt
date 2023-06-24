Problem taken from: https://web.archive.org/web/20141023152658/http://www.rgmadvisors.com/problems/orderbook/

Data files taken from https://github.com/panaali/orderbook/tree/master/data
---------------------------------------------------------------

Solving Pricer using two heaps stored in an OrderBook class

Each order is its own class, and there's an "orders" dictionary that maps ids to the instances of the class. My implementation first implements an orderbook using a minheap for asks and a maxheap for bids. 

Next, to output the buy and sell prices, I sort the respective heap, and then implement a quick while loop to compute the price of buying/selling target_size shares (if possible).

Theoretical runtimes:
- Adding in an order takes O(log(n)) time, where n is the size of the order book
- Resizing an order takes O(1) time because of the order dictionary
- Checking the price of buying/selling is O(n) time

Bottlenecks/inefficiencies:

- My implementation requires frequent re-sorting of the bids and asks lists. This is to make the pricing algorithm simpler
- My implementation of the pricing angorithm is not very good. It first sorts the orderbook, then runs through it to find the price of the buy/sale. A better algorithm would exploit the heap structure, and make changes to the price only as-needed.
