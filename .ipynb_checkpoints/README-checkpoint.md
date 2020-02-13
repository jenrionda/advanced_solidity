# Unit 21: You sure can attract a crowd!

![crowd](https://image.shutterstock.com/image-photo/group-people-holding-cigarette-lighters-600w-687342115.jpg)

## Background

My company has decided to crowdsale the PupperCoin token in order to help fund the network development.
This network will be used to track the dog breeding activity across the globe in a decentralized way, and allow humans to track the genetic trail of their pets. I have already worked with the necessary legal bodies and have the green light on creating a crowdsale open to the public. However, I am required to enable refunds if the crowdsale is successful and the goal is met, and I am only allowed to raise a maximum of 300 Ether. The crowdsale will run for 24 weeks.

I will create an ERC20 token that will be minted through a `Crowdsale` contract leveraging the OpenZeppelin Solidity library.

This crowdsale contract will manage the entire process, allowing users to send ETH and get back PUP (PupperCoin).
This contract will mint the tokens automatically and distribute them to buyers in one transaction.

It will need to inherit `Crowdsale`, `CappedCrowdsale`, `TimedCrowdsale`, `RefundableCrowdsale`, and `MintedCrowdsale`.

I will conduct the crowdsale on the Kovan or Ropsten testnet in order to get a real-world pre-production test in.

### Creating the project

Using Remix, created a file called `PupperCoin.sol` and created a standard `ERC20Mintable` token. 

Created a new contract named `PupperCoinCrowdsale.sol`, and prepared it like a standard crowdsale.

### Designing the contracts

#### ERC20 PupperCoin

Used a standard `ERC20Mintable` and `ERC20Detailed` contract, hardcoding `18` as the `decimals` parameter, and leaving the `initial_supply` parameter alone.

#### PupperCoinCrowdsale

Leveraged the `Crowdsale.sol`, saving the file in Remix .

![Initial Setup](Pupper_Step1.png)

Bootstrapped the contract by inheriting the following OpenZeppelin contracts:

* `Crowdsale`

* `MintedCrowdsale`

* `CappedCrowdsale`

* `TimedCrowdsale`

* `RefundablePostDeliveryCrowdsale`

Provided parameters for all of the features of the crowdsale.

Hardcoded a `rate` of 1, to maintain parity with Ether units (1 TKN per Ether, or 1 TKNbit per wei). 

Since `RefundablePostDeliveryCrowdsale` inherits the `RefundableCrowdsale` contract, which requires a `goal` parameter, I call the `RefundableCrowdsale` constructor from the `PupperCoinCrowdsale` constructor as well as the others. `RefundablePostDeliveryCrowdsale` does not have its own constructor, so just use the `RefundableCrowdsale` constructor that it inherits.

When passing the `open` and `close` times, used `now` and `now + 24 weeks` to set the times properly from the `PupperCoinCrowdsaleDeployer` contract.

![Deployed Contract](Pupper_Step2.png)
![Tested Transaction](Pupper_Step3.png)

#### PupperCoinCrowdsaleDeployer

In this contract, modeled the deployment based off of the `ArcadeTokenCrowdsaleDeployer` I previously built. 

Tested the crowdsale by sending Ether to the crowdsale from a different account.

Once confirm that the crowdsale works as expected, added the token to MyCrypto and tested a transaction. 

### Deploying the Crowdsale

Deployed the crowdsale to the Kovan or Ropsten testnet, and store the deployed address for later. Switch MetaMask to your desired network, and use the `Deploy` tab in Remix to deploy your contracts.

![Step ](Crowdsale_Step1.png)
![Step 2](Crowsdale_Step2.png)
![Step 3](Crowdsale_Step3.png)
![Step 4](Crowdsale_Step4.png)
![Step 5](Crowdsale_Step5.png)
![Step 6](Crowdsale_Step6.png)
![Step 7](Crowdsale_Step7.png)
