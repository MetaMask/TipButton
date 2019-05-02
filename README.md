# Pay With MetaMask Buttons

[Live example](https://metamask.github.io/TipButton/)

A variety of MetaMask approved buttons for use on your own website to suggest that your users pay with MetaMask!

Usage is very easy:

```html
<div class="tip-button"></div>
```

```css
.tip-button {
  width: 304px;
  height: 89px;
  background-size: 100%;
  background-image: url('images/1_pay_mm_off.png');
  cursor: pointer;
}

.tip-button:hover {
  background-image: url('images/1_pay_mm_over.png');
}

.tip-button:active {
  background-image: url('images/1_pay_mm_off.png');
}
```

```javascript
var tipButton = document.querySelector('.tip-button');
const tipUser = () => {
    var user_address = web3.eth.accounts[0];
    web3.eth.sendTransaction({
	to: YOUR_ADDRESS,
	from: user_address,
	value: web3.toWei('1', 'ether'),
    }, function (err, transactionHash) {
	if (err) return renderMessage('Oh no!: ' + err.message);
	// If you get a transactionHash, you can assume it was sent,
	// or if you want to guarantee it was received, you can poll
	// for that transaction to be mined first.
	renderMessage('Thanks!');
    });
}
tipButton.addEventListener('click', async () => {
    // Modern dapp browsers...
    if (window.ethereum) {
	window.web3 = new Web3(ethereum);
	try {
	    // Request account access if needed
	    await ethereum.enable();
	    // Acccounts now exposed
	    tipUser();
	} catch (error) {
	    // User denied account access...
	}
    }
    // Legacy dapp browsers...
    else if (window.web3) {
	window.web3 = new Web3(web3.currentProvider);
	// Acccounts always exposed
	tipUser();
    }
    // Non-dapp browsers...
    else {
	console.log('Non-Ethereum browser detected. You should consider trying MetaMask!');
    }
});
```

## The Images

1_pay_mm_off.png
![](images/1_pay_mm_off.png)

1_pay_mm_over.png
![](images/1_pay_mm_over.png)

2_pay_mm_over.png
![](images/2_pay_mm_over.png)

2_pay_mm_off.png
![](images/2_pay_mm_off.png)

3_pay_mm_off.png
![](images/3_pay_mm_off.png)

3_pay_mm_over.png
![](images/3_pay_mm_over.png)

4_pay_mm_off.png
![](images/4_pay_mm_off.png)

4_pay_mm_over.png
![](images/4_pay_mm_over.png)

3_pay_mm_over.png
![](images/3_pay_mm_over.png)

5_pay_mm_off.png
![](images/5_pay_mm_off.png)

5_pay_mm_over.png
![](images/5_pay_mm_over.png)

6_pay_mm_off.png
![](images/6_pay_mm_off.png)

6_pay_mm_over.png
![](images/6_pay_mm_over.png)


