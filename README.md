**[Preview:](https://dieenx.github.io/direct-link-gg/)**
- id view
```
https://docs.google.com/uc?export=view&id=
```
- id download
```
https://docs.google.com/uc?export=download&id=
```

> view-source:
```
<html><head><base target="_blank"></head><body><div class="link-generate">
    <link href="https://fonts.googleapis.com/css2?family=Roboto+Condensed&amp;display=swap" rel="stylesheet">
    <script language="javascript">
        window.onload = setup;

        function setup(){
            document.getElementById("button").addEventListener("click", go);
            document.getElementById("output").addEventListener("click", copy);
        }
        
        function setStatus(status, error = false) {
            var helpText = document.getElementById("help-text");
            
            helpText.innerText = status;
            
            if (error) {
                helpText.style.color = "darkred";
            } else {
                helpText.style.color = "#227300";
            }
        }
          
        function go(){
            var linkId = document.getElementById("input").value;
            var idExtractor = /\/d\/(.+?)(?:\/|#|\?|$)/;
            var result = idExtractor.exec(linkId);
            
            var outputBox = document.getElementById("output");
            
            
            if (!result) {
                outputBox.value = "";
                setStatus("Error: Invalid URL", true);
                outputBox.disabled = true;
                return;
            }
            
            var finalLink = "https://docs.google.com/uc?id=" + result[1];
            outputBox.disabled = false;
            outputBox.value = finalLink;
            setStatus("Success! Click the output link to copy it to your clipboard");
        }
        
        function copy() {
            if (this.disabled) {
                return;
            }
            
            this.select();
            var copied = document.execCommand("copy");
            
            if (copied) {
                setStatus("Link copied to clipboard!");
            } else {
                setStatus("Couldn't copy link to clipboard. Please copy it manually.", true);
            }
        }
    </script>
    <style>
        .link-generate {
            font-family: 'Roboto Condensed', sans-serif;
        }
    
        .title {
            font-size: 1.6em;
            margin: 15px 0 10px;
        }
        
        .sub {
            font-size: 0.5em;
            color: #444;
            vertical-align: middle;
        }
        
        #button {
            display: block;
            font-family: 'Roboto Condensed', sans-serif;
            font-size: 1.2em;
            padding: 10px 18px;
            margin: 15px auto;
            border: none;
            border-radius: 3px;
            background: #ffd54f;
            color: #111;
            cursor: pointer;
            box-shadow: 0 2px 3px 0px #b5b5b5;
            transition: background 200ms;
        }
        
        #button:hover {
            background: #ffe48e;
        }
        
        #button:active {
            background: #ffd54f;
            box-shadow: 0 2px 3px -1px #b5b5b5;
        }
        
        #input, #output {
            font-size: 1.1em;
            display:block;
            width:100%;
            padding: 10px;
            border: 1px solid #b5b5b5;
            border-radius: 3px;
        }
        
        #help-text {
            font-weight: 600;
            margin: 10px;
        }
    </style>
    <div class="title">Enter your sharing URL:&nbsp;<span class="sub">(Scroll down for instructions)</span></div>
    <input id="input" type="text">
    <button id="button">Create Direct Link</button>
    <div class="title">Output link:</div>
    <input id="output" type="text" readonly="" disabled="">
    <div id="help-text"></div>
</div></body></html>
```
