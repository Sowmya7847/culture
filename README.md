<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Music Genre Fusion AI</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #2c3e50, #4ca1af);
            color: white;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .container {
            text-align: center;
            max-width: 600px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
        }

        label {
            font-size: 1.2rem;
            margin: 10px 0;
            display: block;
        }

        select, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
            outline: none;
        }

        button {
            background-color: #4ca1af;
            color: white;
            cursor: pointer;
            transition: 0.3s;
        }

        button:hover {
            background-color: #2c3e50;
        }

        .output {
            margin-top: 20px;
        }

        audio {
            margin-top: 15px;
            width: 100%;
        }

        .loader {
            margin-top: 20px;
            display: none;
        }

        .loader img {
            width: 50px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Music Genre Fusion AI</h1>

        <label for="genre">Select Modern Genre:</label>
        <select id="genre">
            <option value="pop">Pop</option>
            <option value="edm">EDM</option>
            <option value="jazz">Jazz</option>
            <option value="hiphop">Hip-Hop</option>
        </select>

        <label for="culture">Select Cultural Influence:</label>
        <select id="culture">
            <option value="indian">Indian Classical</option>
            <option value="african">African Drumming</option>
            <option value="celtic">Celtic</option>
            <option value="flamenco">Flamenco</option>
        </select>

        <label for="tempo">Select Tempo:</label>
        <select id="tempo">
            <option value="slow">Slow</option>
            <option value="medium">Medium</option>
            <option value="fast">Fast</option>
        </select>

        <button id="generate">Generate Fusion</button>

        <div class="loader">
            <img src="https://media.giphy.com/media/d2ZFV4gL61mDUgTZgE/giphy.gif" alt="Loading..."/>
        </div>

        <div class="output">
            <h3>Generated Music:</h3>
            <audio id="audio" controls></audio>
        </div>
    </div>

    <script>
        const generateButton = document.getElementById("generate");
        const genreSelect = document.getElementById("genre");
        const cultureSelect = document.getElementById("culture");
        const tempoSelect = document.getElementById("tempo");
        const audioPlayer = document.getElementById("audio");
        const loader = document.querySelector(".loader");

        async function fetchFusionMusic(genre, culture, tempo) {
            try {
                loader.style.display = "block"; // Show loader
                // Mock API response for testing in sandboxed environments
                const mockResponse = {
                    audioUrl: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"
                };

                // Simulate fetch with mock response
                await new Promise(resolve => setTimeout(resolve, 2000)); // Simulate network delay
                return mockResponse.audioUrl; // Return mock audio URL
            } catch (error) {
                console.error(error);
                alert("Error generating music. Please try again.");
            } finally {
                loader.style.display = "none"; // Hide loader
            }
        }

        generateButton.addEventListener("click", async () => {
            const genre = genreSelect.value;
            const culture = cultureSelect.value;
            const tempo = tempoSelect.value;

            const audioUrl = await fetchFusionMusic(genre, culture, tempo);

            if (audioUrl) {
                audioPlayer.src = audioUrl;
                audioPlayer.play();
            }
        });
    </script>
</body>
</html>
