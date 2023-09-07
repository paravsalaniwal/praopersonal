---
layout: default
title: Translator
description: Our pair showcase JS project incorporating the Google Translate API
permalink: /translator
type: tangibles
courses: { csa: {week: 2} }
---

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
            margin-top: 10px;
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
        <!-- Add more language options as needed -->
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
                const apiKey = 'f2586bd8c7mshe64d56ce3a69011p10e170jsn51b21e88070f';
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
