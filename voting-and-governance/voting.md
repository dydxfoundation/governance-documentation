---
description: An overview of the voting process.
---

# Voting Process

dYdX v3 is governed and upgraded by Governance Tokens holders and delegatees.

## **Proposing & Voting Powers**

There are two powers associated with each of the Governance Tokens:

* The **proposing power** gives access to creating and sustaining a proposal.
* The **voting power** is used to vote for or against existing proposals.

Governance Tokens holders receive governance powers proportionally to their sum of owned and delegated tokens at a given block.

**`Proposing Power =`**`Proposing Power from $ethDYDX token +`

`Proposing Power from $wethDYDX token +`

`Proposing Power from $stkDYDX token +`

`Proposing Power from $ethDYDX token received as delegatee +`

`Proposing Power from $wethDYDX token received as delegatee +`

`Proposing Power from $stkDYDX token received as delegatee -`

`Proposing Power from $ethDYDX delegated -`

`Proposing Power from $wethDYDX delegated -`

`Proposing Power from $stkDYDX delegated`

\`\`

**`Voting Power =`**`Voting Power from $ethDYDX token +`

`Voting Power from $wethDYDX token +`

`Voting Power from $stkDYDX token +`

`Voting Power from $ethDYDX token received as delegatee +`

`Voting Power from $wethDYDX token received as delegatee +`

`Voting Power from $stkDYDX token received as delegatee -`

`Voting Power from $ethDYDX delegated -`

`Voting Power from $wethDYDX delegated -`

`Voting Power from $stkDYDX delegated`

## FAQ

### How do I vote?

In order to participate in dYdX governance, you will need to have or be delegated the Governance Tokens. You will also need ETH to cover transaction costs.

If you have tokens or have been delegated tokens and there is an active proposal, you are ready to vote in dYdX Governance.

![Cast votes using your voting power](../.gitbook/assets/1-voting-power.png)

To cast your vote, navigate to the proposals page and click on an active proposal.

### **How do I delegate?**

dYdX governance allows holders to delegate voting rights to the address of their choice. Anybody can participate in dYdX governance by receiving delegation, without needing to own Governance Tokens. Users can delegate to one address at a time, and the number of votes added to the delegatee’s vote count is equivalent to the balance of Governance Tokens in the user’s account. Votes are delegated from the current block and onward, until the sender delegates again, or transfers their Governance Tokens.

![Delegate away your voting & proposing powers](../.gitbook/assets/1-delegate-power.png)

Token holders can choose to delegate one or both of the governance powers associated with a token, either through the governance portal or programmatically. A user that has received delegated power can not forward this delegated power to another delegatee.

Token holders can delegate proposing power and voting power to different addresses. However, there is no partial delegation (only 100% or 0% of power.)

To delegate your tokens to a wallet address:

* Go to [dydx.community/dashboard](https://dydx.community/dashboard)
* Click on "Delegate"
* Select type of power you want to delegate
* Enter a Wallet Address for a third party to whom you would like to delegate your voting and/or proposal power to. Delegating powers does not transfer your tokens

Delegating and undelegating Governance Tokens require users to spend Ethereum gas fees.

### Can I change my vote after I have already voted?

Once a vote is cast on-chain, it is not possible to change your vote.

### Can I transfer my Governance Tokens while the vote is in progress?

Yes.

### Can I add more tokens to my vote?

When a DIP is submitted on-chain, a snapshot is taken of current token holders. Users will need to own Governance Tokens before the start block.
