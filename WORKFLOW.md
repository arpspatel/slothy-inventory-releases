# Slothy Inventory Manager: how the workflow works

A walkthrough of recording buys and sells from start to finish: what to enter, what each status means, and how and
when the app changes your inventory, cost and profit. For a page-by-page reference, see the [user guide](GUIDE.md).

- [The big idea](#the-big-idea)
- [Statuses at a glance](#statuses-at-a-glance)
- [The numbers on Inventory](#the-numbers-on-inventory)
- [Recording a buy, step by step](#recording-a-buy-step-by-step)
- [Recording a sell, step by step](#recording-a-sell-step-by-step)
- [How cost and profit are worked out](#how-cost-and-profit-are-worked-out)
- [Shipping and fees](#shipping-and-fees)
- [Buying and selling serialised pieces](#buying-and-selling-serialised-pieces)
- [When things don't go to plan](#when-things-dont-go-to-plan)
- [A daily routine](#a-daily-routine)
- [Month end](#month-end)

## The big idea

**You never type how many of something you have.** Every unit in your inventory got there through a buy, and leaves
through a sell. The app adds up your trades to work out what you have, what it cost and what you made.

A trade only changes your inventory once **you** mark it **✔ Trade Completed**. Until then it's *open*: the app shows
it as on the way in or on the way out, but your on-hand count, average cost and profit don't change. Nothing completes
a trade automatically, not even a "Delivered" from the tracking sync, so you always get to check the package first.

```
 Buy:   create ──► paid ──► tracking added ──► in transit ──► delivered ──► ✔ completed ──► in inventory
 Sell:  create ──► paid ──► tracking added ──► in transit ──► delivered ──► ✔ completed ──► out of inventory, profit booked
```

## Statuses at a glance

| Status | Means | Where it shows | Changes inventory? |
|---|---|---|---|
| **Ship First/Trade** | Agreed, but the money hasn't moved: one side ships first, or it's a swap | Pending Trades, *unpaid* | No |
| **Awaiting Payment** | Sell agreed, waiting for the buyer to pay (the default for a new sell) | Pending Trades, *unpaid* | No |
| **Payment Completed** | Paid (the default for a new buy), not shipped yet | Pending Trades | No |
| **Trade Pending** | A tracking number is on the trade: the package is with the carrier | Pending Trades | No |
| **Delivered** | Tracking says it arrived (set by a tracking sync, or by you). The row turns green | Pending Trades, *Needs attention* | No |
| **✔ Trade Completed** | You checked it and it's done | Trade History | **Yes** |
| **Lost/No Refund** | It never arrived and no money came back | Trade History | **Yes** (see [below](#lost-in-the-mail)) |
| **Cancelled** | The deal fell through | Trade History | No, it's ignored everywhere |

You can always change a status by hand in the trade, but most of the time the buttons and the tracking sync move a
trade along for you.

## The numbers on Inventory

Each item shows several quantities. They're all worked out from your trades:

| Column | What it counts |
|---|---|
| **On hand** | Units from completed buys, minus units from completed sells. What's physically yours |
| **Incoming** | Units on open buys: paid for or agreed, not arrived and completed yet |
| **Sell pending** | Units on open sells: promised to a buyer, still on hand until the sell is completed |
| **Available** | On hand − Sell pending. What you can still offer to someone else |
| **For sale** | Units you've listed, after any open sells use them up (never more than Available) |
| **Avg cost/u** | Average price you paid for the units on hand (see [cost](#how-cost-and-profit-are-worked-out)) |
| **Sold** / **Realized P/L** | Units sold on completed sells, and the profit made on them |

The app won't let a sell take more than is *Available*, so you can't promise the same coin to two buyers.

## Recording a buy, step by step

The example used throughout: you buy **10 × 1 oz Silver Eagle at $32 each** from `seller456` on Reddit.

### 1. Create the buy

Click **New buy** (Ctrl+B, the Quick actions, or **＋ Buy from** on a counterparty) and fill in:

| Field | What to enter |
|---|---|
| **Date** | The day you agreed the deal |
| **Counterparty** / **Counterparty type** | Start typing to pick someone you've traded with; a new name is saved with the trade. Type: Reddit (P2P), eBay, Whatnot, Online, Coin Shop or Coin Show |
| **Status** | **Payment Completed** if you've paid (the default), **Ship First/Trade** if you haven't yet |
| **Post / order link** | The Reddit post, eBay listing or order page, so you can find it again |
| **Ship method**, **Shipping $**, **Fees $** | What you paid for shipping and any payment fees (see [shipping and fees](#shipping-and-fees)) |
| **Payment method** / **Payment detail** | Zelle, Venmo, PPFF, Cash App, Credit Card, Cash or another; the username, phone, email or a card's last 4 digits |
| **Tracking #** | When the seller sends it (you can add it later) |
| **Address**, **Notes** | Anything you want to keep with the trade |

Then add the items, one line each:

1. In **Item**, pick something you already have, or click **New item…** to add it (metal, name, mint, weight and unit,
   grade, serial and so on).
2. Enter **Qty** and **Unit price $**, then click **Add line**.
3. For a lot bought at one total price, add all the lines and use **Lot price…** to split the total across them.

Click **Save**. The buy is now in **Pending Trades**, and Inventory shows the 10 Eagles as **Incoming: 10**. On hand
hasn't changed.

### 2. Paid or not

If you saved it as **Ship First/Trade**, it shows **· unpaid**. Once you've paid, click **$ Payment Completed** in
Pending Trades. The app tracks *paid* separately from shipping, so adding a tracking number to an unpaid trade doesn't
make it look paid.

### 3. Add tracking

When the seller ships, open the trade and type the **Tracking #**. Saving it moves the trade to **Trade Pending**.

If you use ParcelApp, click **➕ Add to ParcelApp** (on the Dashboard or Pending Trades) to start tracking it. After
that, **⟳ Sync tracking** updates the tracking status and expected date. See the
[user guide](GUIDE.md#tracking-with-parcelapp) for ParcelApp's daily limits.

### 4. Delivered

When tracking shows it arrived, a sync sets **Delivered** and the row turns green. Nothing has changed in your
inventory yet: open the package and check it's what you paid for.

### 5. Complete it

Select the trade and click **✔ Trade Completed**. Now:

- the trade moves to **Trade History**, with today as its completed date (to record an earlier day, fill in the
  trade's **Completed date** first);
- Inventory shows **On hand: 10**, **Incoming: 0** and **Avg cost/u: $32.00**;
- the shipping and fees you entered appear on the **Expenses** page.

If only some of the items arrived, use **Partly delivered…** instead (see [below](#only-part-of-it-arrived)).

## Recording a sell, step by step

Continuing the example: you later buy **5 more Eagles at $35** (now 15 on hand, average $33.00) and list them. Then
`buyer123` agrees to buy **6 at $40 each**.

### 1. List it (optional)

On **Inventory**, select the item and click **List for sale…**. Enter how many and your asking price per unit: say
**10 at $40**. The item now appears on the **For Sale** page.

### 2. Create the sell

Either:

- on **For Sale**, select the listing and click **Sell selected…**: the quantity and price are filled in from the
  listing, and you change the Qty to 6; or
- click **New sell** (Ctrl+S), pick the item, and enter **Qty 6** and **Unit price $40**.

Fill in the counterparty and the other fields as for a buy. Here **Shipping $** is what the **buyer paid you** for
shipping (0 if shipping was free). The status starts as **Awaiting Payment**.

Click **Save**. Now:

| | Before | After saving the sell |
|---|---|---|
| On hand | 15 | 15 (it's still yours until the sell is completed) |
| Sell pending | 0 | 6 |
| Available | 15 | 9 |
| For sale | 10 | 4 (the sell used up 6 of the 10 listed) |

### 3. Get paid

When the buyer pays, click **$ Payment Completed**. If you ship before they pay, set **Ship First/Trade**; the trade
stays marked *unpaid* until you mark it paid.

### 4. Pack and ship

1. In **Pending Trades**, click **🖨 Packing slips**, tick this sell and click **Print selected**. You get a 4x6 slip
   with **username · name · tracking** and each item on its own line, so you can check the coins against the slip as
   you pack. Several slips fit on one label, with a cut line between them.
2. Buy the shipping label, then type its **Tracking #** into the trade. It moves to **Trade Pending**.
3. Click **➕ Add to ParcelApp** if you want to track it.

### 5. Delivered and completed

When tracking shows **Delivered**, confirm with the buyer that everything arrived, then click **✔ Trade Completed**.
Now:

- On hand drops from 15 to **9**, and Sell pending goes back to 0.
- The sale is booked: **sale price $240**, **cost $198** (6 × the $33.00 average), **P/L +$42**.
- The 6 units come off the listing for good, so For sale stays at 4.
- The sale shows in **Trade History**, both **By trade** and **By item sold**, and counts in **Reports** in the month
  you completed it.

## How cost and profit are worked out

The app uses the **weighted average cost** method, applied in the order trades were completed.

| Event | On hand | Total cost of what's on hand | Avg cost/u |
|---|---|---|---|
| Buy 10 at $32, completed | 10 | $320 | $32.00 |
| Buy 5 at $35, completed | 15 | $495 | $33.00 |
| Sell 6 at $40, completed | 9 | $495 − 6 × $33 = $297 | $33.00 |

- A **buy** adds its units and what you paid for them, so the average moves toward the new price.
- A **sell** takes units out at the current average cost; that's the sale's **cost basis**. The sale's
  **P/L = sale price − cost basis**: $240 − $198 = **+$42**. Selling never changes the average cost of what's left.
- Cost is the price of the metal only. Shipping and fees are counted as expenses, not added to cost.
- **Net P/L** (Dashboard, Reports) = sales − cost of sales − lost buys written off − expenses.
- **Sold before it was recorded as bought?** If you complete a sell before the buy that supplied it, the item is
  flagged as *oversold* because there's no cost to take yet. When you complete the buy, its cost goes to that sale, in
  the sale's month, and the flag clears.

## Shipping and fees

On every trade:

- **Shipping $**: on a buy, what you paid the seller for shipping. On a sell, what the buyer paid you for shipping.
- **Fees $**: payment fees, such as PayPal Goods & Services.

These appear on the **Expenses** page as ⇄ rows, dated by the trade, so don't enter them again by hand. They never
change an item's cost or a sale's price, but they're included in net P/L.

What a shipping label really cost comes from your label provider. Upload its export file in **Expenses → Shipping
labels…** (a Pirate Ship export works as it is). Each label is matched to the trade with the same tracking number:

| Trade | Shipping $ on the trade | Label cost | Result in Ship +/− |
|---|---|---|---|
| Buy | $8 paid | none | −$8 |
| Sell, buyer paid shipping | $6 collected | $5.20 | +$0.80 |
| Sell, free shipping | $0 | $5.20 | −$5.20 |
| Sell, label not uploaded yet | $6 collected | waiting | +$6, marked **?** |

A label that doesn't match a trade isn't counted until you decide: link it to a trade, count it as an expense, or
don't count it.

Other costs (mailers, capsules, flips, subscriptions) go on the **Expenses** page as Shipping, Materials, Fees or
Other.

## Buying and selling serialised pieces

Bars and coins with a serial number are tracked one by one. Each serial is its own item with its own cost and history,
and pieces that share metal, name, mint, weight and grade are grouped as one **product** on Inventory.

**Buying serialised pieces:**

1. Select the product on Inventory and click **Buy more…**, or pick the `▣` product in the buy's Item box.
2. Type or paste the serials into the **Serials** box: one per line, separated by commas, or as a range like
   `1984-2000`. The quantity follows the number of serials.
3. Save. Each serial becomes its own item when the buy is saved. Cancelling creates nothing.

**Don't know the serials yet?** Buy the item without serials (for example, Qty 3). When it arrives, **Edit** the item
and type the serials, comma-separated, in *Cert / serial no*. It's split into one item per serial at the same cost.
If only some have arrived, type just those; add the rest when they come.

**Selling serialised pieces:** select the serial rows you're selling (Ctrl- or Shift-click for several) and click
**Sell selected…**. Or select the product row and pick serials from the list. Each serial is its own line on the sell,
so its own cost is used for the profit.

## When things don't go to plan

### Only part of it arrived

Right-click the trade in Pending Trades (or use **More ▾**) and choose **Partly delivered…**. Enter how many of each
line arrived. That part is completed on the original trade, which keeps its tracking, shipping and fees. The rest moves
to a new open trade with the same counterparty and prices, as Payment Completed and without tracking. Add the second
tracking number to it when it ships.

### Lost in the mail

If a package never arrives and no money comes back, set **Lost/No Refund**:

- **Lost buy:** nothing is added to your inventory, and what you paid is written off as a loss.
- **Lost sell:** the items leave your inventory and it's booked as a sale, because you kept the payment.

If insurance or a refund comes through later, record it with **Return / refund…** in Trade History (see below).

### The deal fell through

Set **Cancelled**. A cancelled trade stays in Trade History for your records but counts nowhere: not in inventory,
P/L or expenses.

### You made a mistake on a completed trade

In Trade History, right-click the trade and choose **Reopen**. It goes back to Pending Trades and its effect on
inventory and P/L is undone. Fix it, then complete it again. The app asks whether to keep the original completed date,
so a sale stays in its month.

### Returns and refunds after a trade is finished

Use **Return / refund…** in Trade History. It's recorded on its own date, so the original month's numbers stay as they
were and the change lands in the month it happened:

| What happened | Enter | Effect |
|---|---|---|
| Buyer sent units back | units and the refund | units back on hand at the cost they left with; that part of the sale is reversed |
| Buyer kept it, you refunded part | refund only | the sale price goes down |
| You sent units back to the seller | units and the refund | units leave at the average cost; any difference is a gain or loss |
| Seller refunded part, you kept it | refund only | lowers the cost of what you have on hand |
| Money back on a lost buy | money back | reduces the loss written off |
| Lost sell, you refunded the buyer | refund | reverses the sale |
| Insurance paid out | amount received | income against what was written off |

A trade with a return or refund shows **↩**. Remove the return before reopening the trade or changing its items.

## A daily routine

1. **Open the app.** It fetches spot prices and syncs tracking once by itself.
2. **Check *Needs attention*** on the Dashboard: unpaid trades, delivered trades waiting for you, failed tracking adds.
3. **New deals:** record each buy and sell as soon as it's agreed, so *Available* stays right and you don't promise
   the same piece twice.
4. **Payments:** click **$ Payment Completed** as money comes in or goes out.
5. **Shipping out:** print packing slips, pack, add tracking numbers, then **➕ Add to ParcelApp**.
6. **Arrivals:** for each **Delivered** buy, check the package, then **✔ Trade Completed**. For each delivered sell,
   confirm with the buyer, then complete it.

## Month end

1. **Expenses:** add any costs that weren't on a trade (supplies, subscriptions).
2. **Shipping labels:** upload your label provider's latest export, then decide on any labels that didn't match a
   trade.
3. **Open trades:** anything still in Pending Trades doesn't count yet. Complete what's done, so it lands in this month.
4. **Reports:** check the month's sales, cost, expenses and net P/L. Click the month's bar for a breakdown, and use
   **Export CSV…** or **File → Export to Excel…** for your records.
