---
layout: default
title: Translator
description: Our pair showcase JS project incorporating the Google Translate API
permalink: /translator
type: tangibles
courses: { csa: {week: 3} }
---

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