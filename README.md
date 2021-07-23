# Password Generator by Filip

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)

![htmlBadge](https://img.shields.io/badge/HTML-239120?style=for-the-badge&logo=html5&logoColor=white)
![cssBadge](https://img.shields.io/badge/CSS-239120?&style=for-the-badge&logo=css3&logoColor=white)
![jsBadge](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

**Live Demo ➢** [Click Here](https://password-generator-filip.netlify.app/)


**Features** :rocket:
- Length Picker
- Choose what characters to include (ex. symbols, numbers, etc)
- Copy password to Clipboard 

<br/><br/>
<br/><br/>

**Code Explained** :key:
<br></br>
All source code is on my github

-  *Javascript*

    -   Getting random letters, numbers, etc.
    <br/><br/>
    ```javascript
    function getRandomUpper() {
	return String.fromCharCode(Math.floor(Math.random() * 26) + 65);
    }
    ```
    This function uses [Char Code](http://stevehardie.com/2009/09/character-code-list-char-code/) to get random characters. Upper case letters are from #65 to #90 so the function gets a random number between 1 and 26 and adds 65 to it so it can get a uppercase letter from Char Code

    - Combing the random characters to form password
    <br></br>
    ```javascript
    function generatePassword(lower, upper, number, symbol, length) {
	let generatedPassword = '';
	const typesCount = lower + upper + number + symbol;
	const typesArr = [{lower}, {upper}, {number}, {symbol}].filter(item => Object.values(item)[0]);
	
	// Doesn't have a selected type
	if(typesCount === 0) {
		return '';
	}
	
	// create a loop
	for(let i=0; i<length; i+=typesCount) {
		typesArr.forEach(type => {
			const funcName = Object.keys(type)[0];
			generatedPassword += randomFunc[funcName]();
		});
	}
	
	const finalPassword = generatedPassword.slice(0, length);
	
	return finalPassword;
    }
    ```
    Above is the function that creates the final password using the random characters we generated previously.






