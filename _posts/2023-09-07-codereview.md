---
layout: post
title: Pair Showcase Code Review
permalink: /codereview
type: tangibles
courses: { csa: {week: 3} }
---

<html>
<head>
    <title>Code Review</title>
    <style>
        h1 {
            font-size: 50px;
            text-align: center;
            margin-top: 50px;
            color: #ff8200;
        }
        h2 {
            font-size: 24px;
            text-align: center;
        }
        table {
            width: 1000px;
            border-collapse: separate;
            margin: 0 auto;  
            background-color: #58595b;
        }
        th, td {
            border: 1.5px dashed #ff8200;
            padding: 10px 10px;
            text-align: center;
            width: 333px;
        }
        th {
            background-color: #333;
            color: #ffffff;
        }
        td {
            color: #ff8200;
        }
        a {
            color:black;
        }
        p {
            color: #ff8200;
            margin-left: 0px;
            margin-right: 350px;
            font-size: 27px;
        }
    </style>
</head>
<body>
    <table>
        <thead>
            <tr>
                <th>Aspect</th>
                <th>Good Things</th>
                <th>Improvements</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>HTML Structure</td>
                <td>Well-structured HTML with proper semantic tags.</td>
                <td>
                    <ul>
                        <li>Add meta tags for viewport to ensure mobile responsiveness.</li>
                        <li>Add 'alt' attributes to any future images for accessibility.</li>
                        <li>Add ARIA labels for accessibility.</li>
                    </ul>
                </td>
            </tr>
            <tr>
                <td>CSS</td>
                <td>Specific and straightforward styles.</td>
                <td>
                    <ul>
                        <li>Use CSS variables for colors and common padding/margin values for easier maintenance.</li>
                    </ul>
                </td>
            </tr>
            <tr>
                <td>JavaScript</td>
                <td>Use of modern async/await and fetch API.</td>
                <td>
                    <ul>
                        <li>Add checks for empty text or null values before making API calls.</li>
                        <li>Replace any var with let or const for block-level scoping and better readability.</li>
                        <li>Abstract API calls into a separate function for reusability.</li>
                    </ul>
                </td>
            </tr>
            <tr>
                <td>API Keys</td>
                <td>Correct usage of API key in headers.</td>
                <td>
                    <ul>
                        <li>Store API keys server-side or use environment variables instead of hardcoding them into the client-side code for security reasons.</li>
                        <li>Implement checks for rate limiting or quota exhaustion for the third-party API.</li>
                    </ul>
                </td>
            </tr>
            <tr>
                <td>Error Handling</td>
                <td>Basic try-catch blocks are present.</td>
                <td>
                    <ul>
                        <li>Provide specific error messages to guide the user when something goes wrong.</li>
                        <li>Implement fallback mechanisms such as retrying the request a certain number of times before failing.</li>
                    </ul>
                </td>
            </tr>
            <tr>
                <td>Localization</td>
                <td>Multi-language support through a dropdown menu.</td>
                <td>
                    <ul>
                        <li>Add more languages to the dropdown.</li>
                        <li>Add a label or placeholder for the dropdown to indicate its purpose.</li>
                        <li>Consider auto-detecting the user's preferred language and set it as default.</li>
                    </ul>
                </td>
            </tr>
        </tbody>
    </table>
</body>
</html>

Previous Code:
```
<html>
<head>
    <title>Text Translator</title>
    <style>
        body {
            text-align: center;
        }
        h1 {
            color: #ff8200;
            margin-bottom: 20px;
        }
        textarea {
            width: 50%;
            display:block;
            padding: 10px;
            margin-bottom: 10px;
            margin-right: auto;
            margin-left: auto;
        }
        select {
            padding: 10px;
            display:block;
            margin-left: auto;
            margin-right:auto;
        }
        button {
            padding: 10px 20px;
            background-color: #007bff;
            color: #fff;
            border: none;
            cursor: pointer;
            display:block;
            margin-left: auto;
            margin-right:auto;
            margin-top: 10px;
        }
        #translationResult {
            margin-top: 15px;
            font-weight: bold;
            font-size: 20px;
            text-align: center;
            color: #ff8200;
        }
    </style>
</head>
<body>
    <h1>Text Translator</h1>
    <textarea id="textToTranslate" placeholder="Enter text to translate"></textarea>
    <select id="targetLanguage">
        <option value="en">English</option>
        <option value="es">Spanish</option>
        <option value="fr">French</option>
        <option value="de">German</option>
        <option value="ja">Japanese</option>
        <option value="ar">Arabic</option>
        <option value="pt">Portuguese</option>
        <option value="hi">Hindi</option>
        <option value="zh-TW">Chinese (traditional)</option>
        <option value="fa">Persian</option>
    </select>
    <button id="translateButton">Translate</button>
    <div id="translationResult"></div>
    <script>
        document.addEventListener("DOMContentLoaded", () => {
            const translateButton = document.getElementById("translateButton");
            const textToTranslate = document.getElementById("textToTranslate");
            const targetLanguage = document.getElementById("targetLanguage");
            const translationResult = document.getElementById("translationResult");
            translateButton.addEventListener("click", async () => {
                const text = textToTranslate.value;
                const selectedLanguage = targetLanguage.value;
                const apiKey = '6cf0c105b2mshabcf75f48cea6f9p14945ajsn30b6ebcd6ead';
                const url = 'https://google-translate1.p.rapidapi.com/language/translate/v2/detect';
                const options = {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/x-www-form-urlencoded',
                        'Accept-Encoding': 'application/gzip',
                        'X-RapidAPI-Key': apiKey,
                        'X-RapidAPI-Host': 'google-translate1.p.rapidapi.com',
                    },
                    body: new URLSearchParams({
                        q: text,
                    }),
                };
                try {
                    const response = await fetch(url, options);
                    const data = await response.text();
                    console.log(data);
                    // Extract the detected source language from the response
                    const detectedLanguage = JSON.parse(data).data.detections[0][0].language;
                    // Translate the text to the selected target language
                    const translationUrl = 'https://google-translate1.p.rapidapi.com/language/translate/v2';
                    const translationOptions = {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/x-www-form-urlencoded',
                            'Accept-Encoding': 'application/gzip',
                            'X-RapidAPI-Key': apiKey,
                            'X-RapidAPI-Host': 'google-translate1.p.rapidapi.com',
                        },
                        body: new URLSearchParams({
                            q: text,
                            source: detectedLanguage,
                            target: selectedLanguage,
                        }),
                    };
                    const translationResponse = await fetch(translationUrl, translationOptions);
                    const translationData = await translationResponse.text();
                    console.log(translationData);
                    // Extract the translated text from the response
                    const translatedText = JSON.parse(translationData).data.translations[0].translatedText;
                    translationResult.textContent = `Translation: ${translatedText}`;
                } catch (error) {
                    console.error('Translation error:', error);
                }
            });
        });
    </script>
</body>
</html>
```

<br>
<br>
<br>

New Code:
```
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Text Translator</title>
    <style>
        body {
            text-align: center;
        }
        h1 {
            color: #ff8200;
            margin-bottom: 20px;
            font-size: 45px;
        }
        textarea {
            width: 50%;
            display:block;
            padding: 10px;
            margin-bottom: 10px;
            margin-right: auto;
            margin-left: auto;
        }
        select {
            padding: 10px;
            display: block;
            margin-left: auto;
            margin-right:auto;
        }
        button {
            padding: 10px 20px;
            background-color: #007bff;
            color: #fff;
            border: none;
            cursor: pointer;
            display: block;
            margin-left: auto;
            margin-right:auto;
            margin-top: 15px;
        }
        #translationResult {
            margin-top: 10px;
            font-weight: bold;
            font-size: 20px;
            text-align: center;
            color: #ff8200;
            display: block;
            margin-left: auto;
            margin-right:auto;
        }
        label{
            display: block;
            margin-left: auto;
            margin-right:auto;
            color: #ff8200;
            text-align: center;
            font-size: 20px;
            padding-top: 10px;
            padding-bottom: 10px;
        }
    </style>
</head>
<body>
    <h1>Text Translator</h1>
    <textarea id="textToTranslate" aria-label="textToTranslate" placeholder="Enter text to translate"></textarea>
    <label for="targetLanguage">Select Target Language:</label>
    <select id="targetLanguage" aria-label="targetLanguage">
        <option value="en">English</option>
        <option value="es">Spanish</option>
        <option value="fr">French</option>
        <option value="de">German</option>
        <option value="ja">Japanese</option>
        <option value="ar">Arabic</option>
        <option value="pt">Portuguese</option>
        <option value="hi">Hindi</option>
        <option value="zh-TW">Chinese (traditional)</option>
        <option value="fa">Persian</option>
    </select>
    <button id="translateButton">Translate</button>
    <div id="translationResult"></div>
    <script>
        async function detectLanguage(text, apiKey) { // defining an async function to detect the language of the text
            const url = 'https://google-translate1.p.rapidapi.com/language/translate/v2/detect';
            const options = { // define the options for the http POST request to the language detection API
                method: 'POST',
                headers: {
                    'Content-Type': 'application/x-www-form-urlencoded',
                    'Accept-Encoding': 'application/gzip',
                    'X-RapidAPI-Key': apiKey,
                    'X-RapidAPI-Host': 'google-translate1.p.rapidapi.com',
                },
                body: new URLSearchParams({ q: text }), // send the text to the API as a parameter named 'q'
            };
            const response = await fetch(url, options); // send the request to the API and wait for the response
            const data = await response.json(); // parsing the response as JSON
            return data.data.detections[0][0].language; // extract and return the detected language from the API response
        }
        async function translate(text, source, target, apiKey) { // define an async function to translate text
            const url = 'https://google-translate1.p.rapidapi.com/language/translate/v2';
            const options = {   // define options for the http POST request to the translation API
                method: 'POST',
                headers: {
                    'Content-Type': 'application/x-www-form-urlencoded',
                    'Accept-Encoding': 'application/gzip',
                    'X-RapidAPI-Key': apiKey,
                    'X-RapidAPI-Host': 'google-translate1.p.rapidapi.com',
                },
                body: new URLSearchParams({ q: text, source, target }), // send the text, source language, and target language to the API
            };
            const response = await fetch(url, options); // send the request to the translation API and wait for the response
            const data = await response.json(); // parse the response as JSON
            return data.data.translations[0].translatedText;  // extract and return the translated text from the API response
        }
        document.addEventListener("DOMContentLoaded", () => {     // run code after the DOM (web page) has been fully loaded
            const apiKey = '6cf0c105b2mshabcf75f48cea6f9p14945ajsn30b6ebcd6ead';
            const translateButton = document.getElementById("translateButton");
            const textToTranslate = document.getElementById("textToTranslate");
            const targetLanguage = document.getElementById("targetLanguage");
            const translationResult = document.getElementById("translationResult");
            translateButton.addEventListener("click", async () => {
                const text = textToTranslate.value.trim();   // get the text to translate and the selected target language from the user input
                const selectedLanguage = targetLanguage.value;
                if (!text || !selectedLanguage) {
                    return;
                }
                const detectedLanguage = await detectLanguage(text, apiKey);
                const translatedText = await translate(text, detectedLanguage, selectedLanguage, apiKey); // translate the text from the detected language to the selected target language
                translationResult.textContent = `Translation: ${translatedText}`; // display final translated text
            });
        });
    </script>
</body>
</html>
```

<br>
<br>
<br>

RapidAPI Usage Error:


![](https://github.com/paravsalaniwal/personal/assets/111609656/dca0c06e-bd80-4a26-9a68-13b63f3384a4)