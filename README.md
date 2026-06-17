<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Fun Facts</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            max-width: 600px;
            width: 100%;
            padding: 50px 40px;
            text-align: center;
        }

        h1 {
            color: #333;
            margin-bottom: 10px;
            font-size: 2.5em;
        }

        .subtitle {
            color: #666;
            margin-bottom: 40px;
            font-size: 1.1em;
        }

        .fact-box {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px;
            border-radius: 15px;
            min-height: 150px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 30px;
            font-size: 1.3em;
            line-height: 1.6;
            font-weight: 500;
            transition: all 0.3s ease;
        }

        .fact-box:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
        }

        .button-group {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
        }

        button {
            background: #667eea;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 1em;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        button:hover {
            background: #764ba2;
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.4);
        }

        button:active {
            transform: translateY(0);
        }

        .secondary-btn {
            background: #f0f0f0;
            color: #667eea;
        }

        .secondary-btn:hover {
            background: #e0e0e0;
            color: #764ba2;
        }

        .fact-counter {
            color: #999;
            font-size: 0.9em;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎉 Fun Facts</h1>
        <p class="subtitle">Discover something amazing!</p>
        
        <div class="fact-box" id="factBox">
            Click "New Fact" to get started!
        </div>

        <div class="button-group">
            <button onclick="getRandomFact()">📌 New Fact</button>
            <button class="secondary-btn" onclick="location.reload()">🔄 Refresh</button>
        </div>

        <div class="fact-counter" id="counter"></div>
    </div>

    <script>
        const facts = [
            "Honey never spoils. Archaeologists have found 3,000-year-old honey in Egyptian tombs that was still edible!",
            "A group of flamingos is called a 'flamboyance'.",
            "Octopuses have three hearts and blue blood.",
            "The shortest war in history lasted only 38 minutes between Britain and Zanzibar in 1896.",
            "Bananas are berries, but strawberries aren't.",
            "A mantis shrimp can see 16 color receptors, while humans can only see 3.",
            "Cleopatra lived closer to the moon landing than to the construction of the Great Pyramid.",
            "Tardigrades (water bears) can survive in the vacuum of space.",
            "There are more stars in the universe than grains of sand on all Earth's beaches.",
            "A day on Venus is longer than its year.",
            "Koalas have fingerprints almost identical to humans.",
            "The smell of petrichor (rain on dry earth) is caused by bacteria spores called actinomycetes.",
            "Sharks have been around for over 400 million years—longer than dinosaurs.",
            "Your nose can remember up to 50,000 different scents.",
            "A group of crows is called a 'murder'.",
            "Wombat poop is cube-shaped to prevent it from rolling away.",
            "The Eiffel Tower can be 15 cm taller during summer due to thermal expansion.",
            "Penguins have knees—they're just hidden under their feathers.",
            "A sneeze can travel up to 26 feet (8 meters).",
            "Polar bears have black skin under their white fur."
        ];

        let currentFactIndex = -1;

        function getRandomFact() {
            const randomIndex = Math.floor(Math.random() * facts.length);
            currentFactIndex = randomIndex;
            
            const factBox = document.getElementById('factBox');
            factBox.style.opacity = '0';
            
            setTimeout(() => {
                factBox.textContent = facts[randomIndex];
                factBox.style.opacity = '1';
                document.getElementById('counter').textContent = 
                    `Fact ${randomIndex + 1} of ${facts.length}`;
            }, 200);
        }

        // Load a random fact on page load
        window.onload = getRandomFact;

        // Add fade transition
        const style = document.createElement('style');
        style.textContent = `
            #factBox {
                transition: opacity 0.3s ease;
            }
        `;
        document.head.appendChild(style);

        // Allow keyboard navigation
        document.addEventListener('keydown', (event) => {
            if (event.code === 'Space') {
                event.preventDefault();
                getRandomFact();
            }
        });
    </script>
</body>
</html>