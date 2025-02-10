# youtube-captioner 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouTube Video Captioner</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 20px;
        }
        input, button {
            margin: 10px;
            padding: 10px;
        }
        iframe {
            width: 560px;
            height: 315px;
            margin-top: 20px;
        }
        #caption {
            font-size: 18px;
            margin-top: 10px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <h2>YouTube Video Captioner</h2>
    
    <label>https://youtu.be/OZKZJkIVanY?si=E6jjRAUG9cEYFm9W:</label>
    <input type="text" id="videoLink" placeholder="Paste YouTube link here">
    
    <br>
    
    <label>Enter Caption:</label>
    <input type="text" id="captionText" placeholder="Enter caption here">
    
    <br>
    
    <button onclick="loadVideo()">Load Video</button>
    
    <div id="videoContainer"></div>
    <p id="caption"></p>

    <script>
        function loadVideo() {
            let url = document.getElementById("videoLink").value;
            let caption = document.getElementById("captionText").value;
            let videoId = extractVideoID(url);

            if (videoId) {
                document.getElementById("videoContainer").innerHTML = 
                    `<iframe src="https://www.youtube.com/embed/${videoId}" frameborder="0" allowfullscreen></iframe>`;
                document.getElementById("caption").innerText = caption;
            } else {
                alert("Invalid YouTube link. Please enter a valid URL.");
            }
        }

        function extractVideoID(url) {
            let regex = /(?:youtube\.com\/(?:[^\/]+\/.+\/|(?:v|e(?:mbed)?)\/|.*[?&]v=)|youtu\.be\/)([^"&?\/\s]{11})/;
            let match = url.match(regex);
            return match ? match[1] : null;
        }
    </script>

</body>
</html>
