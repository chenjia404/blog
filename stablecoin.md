# 基于套利机制自适应价格可Staking的算法稳定币

目前区块链生态中，大多数问题都是由一个中心化的机构进行发行，容易出现单点故障，去中心化的稳定币，能更好的用于支持整个生态的发展，本文提出一个基于去中心化交易所做价格指数，使用智能合约编程进行自适应条件的一个去中心化稳定币系统。

## 原理简述

用户把token出售给智能合约，铸造相应的 usd ，用户可以使用 usd 换回 token，销毁相应的  usd ，合约内一直把 usd 的价格按 1usdt 进行处理，进而形成套利空间，套利者会根据市场的供求进行 usd 的铸造和销毁，进而在保证供给量的情况下稳定 usd 价格。

 usd 价格大于1usdt时，矿工可以使用 1usdttoken通过合约兑换获得 1 usd ， usd  价格小于 1usdt 时，矿工可以使用 1 usd  向合约购买价值 1usdt 的 token。矿工在通过token购买 usd 的时候，会先检查用户在合约内token的余额，不足就补充。矿工使用 usd 购买token的时候，token 先存储到合约内的余额，矿工需要的时候可以提现到自己的钱包，或者用于下次套利。

单次铸币不能超过 usd ->usdt流动池的1%，token->usdt价格使用过去5分钟时间加权平均价格(TWAP)，防御闪电贷攻击。

 usd  发生的每笔交易将会被收取 0.3% 的费用，上限为 1usd ，90%分配给 usd Staking用户，10%分配给开发者团队。

 usd  的持有者可以进行Staking， usd 放入 Staking 池，获得手续费分红。

使用token做担保物进行铸造稳定币，远高于比单纯的 ampl 算法稳定币。矿工可以在 usd 波动的时候，进行搬砖套利，同时维护 usd 的价格稳定。同时随着 usd 的使用变多，需要的token担保物也增加多，把更多的token进行锁仓，推动token的价格上涨，同时增加了 usd 的担保物价值，进一步的保证了 usd 的价格。另外矿工也可以锁仓 usd 进行 Staking ，获取 usd 转账手续费分红，同时锁仓 usd 也会加强 usd 价格稳定性。锁仓 usd 进行 Staking 挖矿的收益来自于转账手续费，并不是增发而来，保证了没有零成本的 usd ，没有通胀压力。

## 主要的收益来源

 usd  价格波动的套利。
 usd  Staking 获得手续费分红。

## 主要的潜在风险

token的价格贬值会导致 usd 担保物贬值，如果这个时候再出现挤兑，就会抵押不足。

智能合约代码的漏洞，可能会导致各种攻击发生。

usd 持有者私钥被盗导致大量抛售，导致 usd 价格发生踩踏，继而大量的token从合约里面流出，进而发生token的价格踩踏。

token 被大规模的衍生品使用，碰到连环踩踏强平，会导致抵押不足。