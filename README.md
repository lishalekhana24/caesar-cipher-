# caesar-cipher-
plain text can me easily converted to caesar cipher 
<!DOCTYPE html>
<html>
<head>
    <title>Caesar Cipher Encryption and Decryption Tool</title>
    <style>
        body {
            background-image: url('pic1.jpg');
            background-size: cover;
            background-repeat: no-repeat;
            background-attachment: fixed;
            font-family: Arial, sans-serif;
            color: rgb(243, 234, 234); /* Change this based on your background image */
        }
        h1, h2, label, p {
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7); /* Make text readable over the background image */
        }
        .container {
            background-color: rgba(0, 0, 0, 0.5); /* Optional: darkens the background behind text */
            padding: 20px;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Caesar Cipher Encryption and Decryption Tool</h1>

        <label for="text">Enter your text:</label>
        <input type="text" id="text">

        <label for="shift">Enter shift value:</label>
        <input type="number" id="shift" value="0">

        <button onclick="performEncryption()">Encrypt</button>
        <button onclick="performDecryption()">Decrypt</button>

        <h2>Result:</h2>
        <p id="result"></p>
    </div>

    <script>
        function encryptCaesarCipher(text, shift) {
            let encryptedText = '';
            for (let i = 0; i < text.length; i++) {
                let char = text.charCodeAt(i);
                if (text[i].match(/[a-z]/i)) {
                    let shiftAmount = (text[i] === text[i].toUpperCase()) ? 65 : 97;
                    let encryptedChar = String.fromCharCode((char - shiftAmount + shift) % 26 + shiftAmount);
                    encryptedText += encryptedChar;
                } else {
                    encryptedText += text[i];
                }
            }
            return encryptedText;
        }

        function decryptCaesarCipher(encryptedText, shift) {
            return encryptCaesarCipher(encryptedText, -shift);
        }

        function performEncryption() {
            let text = document.getElementById('text').value;
            let shift = parseInt(document.getElementById('shift').value);
            let encryptedText = encryptCaesarCipher(text, shift);
            document.getElementById('result').innerText = encryptedText;
        }

        function performDecryption() {
            let text = document.getElementById('text').value;
            let shift = parseInt(document.getElementById('shift').value);
            let decryptedText = decryptCaesarCipher(text, shift);
            document.getElementById('result').innerText = decryptedText;
        }
    </script>
</body>
</html>
