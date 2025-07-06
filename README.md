# audits
if (token != address(0)) {

IERC20(token).safeTransferFrom(msg.sender, treasury, amount);

} else {

require(msg.value == amount, "RBNTPresale: Wrong BNB amount");

(bool success, ) = payable(treasury).call{value: amount}("");

require(success, "RBNTPresale: Failed send BNB");

int256 usdPrice = IEACAggregatorProxy(aggregatorBnb2Usd)

.latestAnswer();

amount = (amount * uint256(usdPrice)) / 10 ** 8;

}

...

if (token != address(0)) {

IERC20(token).safeTransferFrom(msg.sender, treasury, amount);

} else {

require(msg.value == amount, "RBNTPresale: Wrong ETH amount");

(bool success, ) = payable(treasury).call{value: amount}("");

require(success, "RBNTPresale: Failed send ETH");

int256 usdPrice = IEACAggregatorProxy(aggregatorEth2Usd)

.latestAnswer();

amount = (amount * uint256(usdPrice)) / 10 ** 8 / 10 ** 12;

}


Smart Contract Audit Reports.
