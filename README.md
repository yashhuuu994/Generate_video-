48 lines

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prompt to Video App</title>
    <style>
        /* Some basic CSS */
        body { font-family: Arial, sans-serif; }
        #container { max-width: 800px; margin: auto; }
        #output { margin-top: 20px; }
    </style>
</head>
<body>
    <div id="container">
        <h1>Prompt to Video Converter</h1>
        <textarea id="prompt" rows="4" cols="50" placeholder="Enter your prompt here..."></textarea>
        <button id="generate">Generate Video</button>
        <div id="output"></div>
    </div>
    <script>
        // JavaScript code here
        document.getElementById('generate').addEventListener('click', function() {
            const promptText = document.getElementById('prompt').value;
            if (promptText.trim() === '') {
                alert('Please enter a prompt.');
                return;
            }
            
            // For now, just display the text and speak it
            const outputDiv = document.getElementById('output');
            outputDiv.innerHTML = `<p>${promptText}</p>`;
            
            // Use SpeechSynthesis
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(promptText);
                speechSynthesis.speak(utterance);
            } else {
                alert('Text-to-speech not supported in your browser.');
            }
            
            // To make it more "video-like", add some animation
            outputDiv.style.animation = 'fadeIn 2s';
        });
