<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meditation App</title>
    <style>
        body {
            font-family: 'Arial, sans-serif';
            background: linear-gradient(to right, #00c6ff, #0072ff);
            color: white;
            text-align: center;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            animation: fadeIn 1s ease-in-out;
        }

        h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
        }

        .form-container {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin: 10px 0 5px;
        }

        input {
            padding: 10px;
            border: none;
            border-radius: 5px;
            width: 100%;
            box-sizing: border-box;
        }

        button {
            margin-top: 15px;
            padding: 10px 20px;
            background-color: #0072ff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
        }

        button:hover {
            background-color: #005bb5;
        }

        .recommendation {
            background: rgba(255, 255, 255, 0.2);
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            display: none;
            animation: slideIn 0.5s ease-in-out;
        }

        h2 {
            font-size: 1.5em;
            margin-bottom: 5px;
        }

        .recommendation img {
            max-width: 100%;
            border-radius: 10px;
            margin-top: 10px;
        }

        .recommendation p {
            color: black;
            font-weight: bold;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        @keyframes slideIn {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Meditation App</h1>
        <div class="form-container">
            <label for="weight">Weight (kg):</label>
            <input type="number" id="weight" name="weight">

            <label for="height">Height (cm):</label>
            <input type="number" id="height" name="height">

            <label for="calories-burnt">Calories Burnt Today:</label>
            <input type="number" id="calories-burnt" name="calories-burnt">

            <label for="calories-intake">Calories Intake Today:</label>
            <input type="number" id="calories-intake" name="calories-intake">

            <label for="age">Age:</label>
            <input type="number" id="age" name="age">

            <button type="button" onclick="showRecommendation()">Get Recommendation</button>
        </div>
        <div class="recommendation" id="recommendation">
            <h2>Recommendation</h2>
            <div id="recommendation-content"></div>
        </div>
    </div>

    <script>
        function showRecommendation() {
            const age = document.getElementById('age').value;
            const recommendation = document.getElementById('recommendation');
            const recommendationContent = document.getElementById('recommendation-content');

            let recommendations = [];

            if (age < 30) {
                recommendations = [
                    { text: 'Try the Mountain Pose for relaxation.', image: 'https://source.unsplash.com/featured/?yoga', audio: 'https://www.example.com/mountain_pose_audio.mp3' },
                    { text: 'Try the Warrior Pose for strength.', image: 'https://source.unsplash.com/featured/?yoga', audio: 'https://www.example.com/warrior_pose_audio.mp3' }
                ];
            } else if (age < 50) {
                recommendations = [
                    { text: 'Try the Tree Pose for balance.', image: 'https://source.unsplash.com/featured/?yoga', audio: 'https://www.example.com/tree_pose_audio.mp3' },
                    { text: 'Try the Bridge Pose for flexibility.', image: 'https://source.unsplash.com/featured/?yoga', audio: 'https://www.example.com/bridge_pose_audio.mp3' }
                ];
            } else {
                recommendations = [
                    { text: 'Try the Seated Forward Bend for flexibility.', image: 'https://source.unsplash.com/featured/?yoga', audio: 'https://www.example.com/seated_forward_bend_audio.mp3' },
                    { text: 'Try the Corpse Pose for relaxation.', image: 'https://source.unsplash.com/featured/?yoga', audio: 'https://www.example.com/corpse_pose_audio.mp3' }
                ];
            }

            recommendations.push({ text: 'Consider a walk in the park for some fresh air.', image: 'https://source.unsplash.com/featured/?park', audio: 'https://www.example.com/walk_park_audio.mp3' });
            recommendations.push({ text: 'Try a cycling session for some cardio.', image: 'https://source.unsplash.com/featured/?cycling', audio: 'https://www.example.com/cycling_audio.mp3' });

            recommendationContent.innerHTML = '';

            recommendations.forEach((rec, index) => {
                setTimeout(() => {
                    const recElement = document.createElement('div');
                    recElement.innerHTML = `
                        <p>${rec.text}</p>
                        <img src="${rec.image}" alt="Recommendation Image">
                        <audio controls>
                            <source src="${rec.audio}" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    `;
                    recElement.style.animation = 'slideIn 0.5s ease-in-out';
                    recommendationContent.appendChild(recElement);
                }, index * 600);
            });

            recommendation.style.display = 'block';
        }
    </script>
</body>
</html>
