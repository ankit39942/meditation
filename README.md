# meditation
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meditation App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            background-color: #f0f8ff;
            margin: 0;
            padding: 20px;
        }
        .container {
            text-align: center;
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #333333;
        }
        form {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        label {
            text-align: left;
        }
        input {
            padding: 10px;
            border: 1px solid #dddddd;
            border-radius: 5px;
        }
        button {
            padding: 10px;
            background-color: #4caf50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        #recommendation {
            margin-top: 20px;
        }
        #suggestedImage {
            max-width: 100%;
            height: auto;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Meditation App</h1>
        <form id="userInputForm">
            <label for="weight">Weight (kg):</label>
            <input type="number" id="weight" name="weight" required>
            
            <label for="height">Height (cm):</label>
            <input type="number" id="height" name="height" required>
            
            <label for="caloriesBurnt">Calories Burnt Today:</label>
            <input type="number" id="caloriesBurnt" name="caloriesBurnt" required>
            
            <label for="caloriesIntake">Calories Intake Today:</label>
            <input type="number" id="caloriesIntake" name="caloriesIntake" required>

            <label for="age">Age:</label>
            <input type="number" id="age" name="age" required>
            
            <button type="submit">Get Recommendation</button>
        </form>
        
        <div id="recommendation">
            <img id="suggestedImage" src="" alt="Meditation Image">
            <audio id="suggestedMusic" controls>
                <source id="audioSource" src="" type="audio/mp3">
                Your browser does not support the audio element.
            </audio>
            <div id="suggestedExercise"></div>
        </div>
    </div>

    <script>
        document.getElementById('userInputForm').addEventListener('submit', function(event) {
            event.preventDefault();

            // Collect user inputs
            const weight = document.getElementById('weight').value;
            const height = document.getElementById('height').value;
            const caloriesBurnt = document.getElementById('caloriesBurnt').value;
            const caloriesIntake = document.getElementById('caloriesIntake').value;
            const age = document.getElementById('age').value;

            // Placeholder logic to suggest media based on age
            let recommendedImage;
            let recommendedMusic;
            let recommendedExercise;

            if (age < 30) {
                recommendedImage = 'https://images.unsplash.com/photo-1506748686214-e9df14d4d9d0'; // Example for age < 30
                recommendedMusic = 'https://cdn.pixabay.com/download/audio/2023/03/23/audio_8d3a2c9b0a.mp3'; // Example for age < 30
                recommendedExercise = `
                    <h3>Recommended Yoga Asanas:</h3>
                    <ul>
                        <li>Surya Namaskar (Sun Salutation)</li>
                        <li>Vrikshasana (Tree Pose)</li>
                        <li>Virabhadrasana (Warrior Pose)</li>
                    </ul>
                    <h3>Recommended Exercises:</h3>
                    <ul>
                        <li>Push-ups</li>
                        <li>Squats</li>
                        <li>Jumping Jacks</li>
                    </ul>
                `;
            } else {
                recommendedImage = 'https://images.unsplash.com/photo-1551334787-21e6bd3ab135'; // Example for age >= 30
                recommendedMusic = 'https://cdn.pixabay.com/download/audio/2023/03/22/audio_6b9c2c7b1c.mp3'; // Example for age >= 30
                recommendedExercise = `
                    <h3>Recommended Yoga Asanas:</h3>
                    <ul>
                        <li>Balasana (Child's Pose)</li>
                        <li>Setu Bandhasana (Bridge Pose)</li>
                        <li>Shavasana (Corpse Pose)</li>
                    </ul>
                    <h3>Recommended Exercises:</h3>
                    <ul>
                        <li>Walking</li>
                        <li>Light Jogging</li>
                        <li>Stretching</li>
                    </ul>
                `;
            }

            // Display the recommended image and music
            const suggestedImageElement = document.getElementById('suggestedImage');
            const suggestedMusicElement = document.getElementById('suggestedMusic');
            const audioSourceElement = document.getElementById('audioSource');
            const suggestedExerciseElement = document.getElementById('suggestedExercise');

            suggestedImageElement.src = recommendedImage;
            suggestedImageElement.style.display = 'block';

            audioSourceElement.src = recommendedMusic;
            suggestedMusicElement.style.display = 'block';
            suggestedMusicElement.load(); // Reload the audio element

            suggestedExerciseElement.innerHTML = recommendedExercise;
        });
    </script>
</body>
</html>
