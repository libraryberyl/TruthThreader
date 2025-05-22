<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>
<style type="text/css">/* --- General Styles --- */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f7f6;
            color: #333;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: flex-start; /* Align to top to prevent jumping */
            min-height: 100vh;
            box-sizing: border-box;
        }

        #game-container {
            background-color: #ffffff;
            border-radius: 12px;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
            padding: 30px;
            width: 100%;
            max-width: 900px;
            box-sizing: border-box;
            text-align: center;
            border: 1px solid #e0e0e0;
        }

        h1 {
            color: #2c3e50;
            font-size: 2.2em;
            margin-bottom: 20px;
        }

        h2 {
            color: #34495e;
            font-size: 1.6em;
            margin-top: 25px;
            margin-bottom: 15px;
        }

        p {
            font-size: 1.1em;
            line-height: 1.6;
        }

        /* --- Buttons --- */
        .game-button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 12px 25px;
            font-size: 1.1em;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.1s ease;
            margin: 10px;
        }

        .game-button:hover {
            background-color: #0056b3;
            transform: translateY(-2px);
        }

        .game-button:active {
            transform: translateY(0);
        }

        .game-button:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
        }

        /* --- Game Introduction --- */
        #game-intro {
            padding: 20px;
            border-bottom: 1px solid #eee;
            margin-bottom: 20px;
        }

        /* --- Credibility Meter --- */
        #credibility-section {
            margin-top: 20px;
            margin-bottom: 30px;
            font-size: 1.1em;
            font-weight: bold;
            color: #555;
        }

        #credibility-bar-container {
            width: 80%;
            max-width: 500px;
            background-color: #e0e0e0;
            border-radius: 10px;
            height: 20px;
            margin: 10px auto 0;
            overflow: hidden;
            border: 1px solid #ccc;
        }

        #credibility-bar {
            height: 100%;
            width: 0%;
            background-color: #28a745; /* Green for good credibility */
            border-radius: 10px;
            transition: width 0.5s ease-in-out;
        }

        /* --- Snippet Card --- */
        #snippet-card {
            background-color: #f8f9fa;
            border: 1px solid #dee2e6;
            border-radius: 10px;
            padding: 25px;
            margin: 25px auto;
            min-height: 120px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            font-size: 1.3em;
            font-style: italic;
            color: #495057;
            max-width: 700px;
        }

        /* --- Source Buttons --- */
        #source-cards {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            margin-top: 30px;
            margin-bottom: 20px;
        }

        .source-button {
            background-color: #6c757d;
            color: white;
            border: none;
            padding: 15px 25px;
            font-size: 1.2em;
            font-weight: bold;
            border-radius: 10px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.1s ease;
            flex: 1 1 180px; /* Allows flexibility in layout */
            max-width: 220px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .source-button:hover:not(:disabled) {
            background-color: #5a6268;
            transform: translateY(-3px);
        }

        .source-button:active:not(:disabled) {
            transform: translateY(0);
        }

        .source-button:disabled {
            background-color: #e9ecef;
            color: #adb5bd;
            cursor: not-allowed;
        }

        .source-button .icon {
            font-size: 1.5em; /* For emoji icons */
        }


        /* --- Feedback Message --- */
        #feedback {
            min-height: 50px;
            font-weight: bold;
            font-size: 1.2em;
            margin-top: 20px;
            padding: 10px;
            border-radius: 8px;
            transition: background-color 0.3s ease, color 0.3s ease;
        }

        .feedback-correct {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }

        .feedback-incorrect {
            background-color: #fff3cd;
            color: #856404;
            border: 1px solid #ffeeba;
        }

        .feedback-misinformation {
            background-color: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }

        /* --- Report Section --- */
        #report-section {
            margin-top: 40px;
            text-align: left;
            border-top: 1px dashed #ccc;
            padding-top: 30px;
        }

        #report-section h3 {
            color: #2c3e50;
            font-size: 1.5em;
            margin-bottom: 20px;
            text-align: center;
        }

        #report-list {
            list-style-type: none;
            padding: 0;
            max-height: 300px; /* Scrollable report */
            overflow-y: auto;
            border: 1px solid #e9ecef;
            border-radius: 8px;
            padding: 15px;
            background-color: #fcfcfc;
        }

        #report-list li {
            background-color: #ffffff;
            border: 1px solid #e6e6e6;
            border-radius: 6px;
            padding: 12px 18px;
            margin-bottom: 10px;
            font-size: 0.95em;
            line-height: 1.5;
            display: flex;
            align-items: flex-start;
            gap: 10px;
        }

        #report-list li .status-icon {
            font-size: 1.2em;
            margin-right: 5px;
        }

        .status-correct { color: #28a745; } /* Green check */
        .status-uncited { color: #ffc107; }  /* Orange warning */
        .status-discredited { color: #dc3545; } /* Red cross */


        /* --- Game End Screen --- */
        #game-end-screen {
            padding: 30px;
            border-top: 1px dashed #ccc;
            margin-top: 30px;
            text-align: center;
        }

        #game-end-screen p {
            font-size: 1.4em;
            font-weight: bold;
            margin-bottom: 20px;
            color: #34495e;
        }

        #game-end-screen .summary-score {
            font-size: 2em;
            color: #007bff;
            margin-bottom: 20px;
        }

        #game-end-screen .summary-message {
            font-size: 1.2em;
            margin-bottom: 30px;
        }

        /* --- Responsive Adjustments --- */
        @media (max-width: 768px) {
            #game-container {
                padding: 20px;
            }

            h1 {
                font-size: 1.8em;
            }

            h2 {
                font-size: 1.4em;
            }

            #snippet-card {
                font-size: 1.1em;
                padding: 20px;
                min-height: 100px;
            }

            .source-button {
                font-size: 1.1em;
                padding: 12px 20px;
                flex: 1 1 120px; /* More flexible for smaller screens */
            }

            #report-list li {
                font-size: 0.9em;
                padding: 10px 15px;
            }
        }

        @media (max-width: 480px) {
            #game-container {
                padding: 15px;
            }
            .source-button {
                flex: 1 1 100%; /* Stack buttons on very small screens */
            }
        }
</style>
<div id="game-container">
<h1>The Truth Threader: Building Credibility, One Citation at a Time</h1>

<div id="game-intro">
<p>Welcome, Junior Researcher! Your mission: To build a definitive, credible report on a fascinating topic by correctly identifying and citing your information sources.</p>

<p>For each piece of information, decide where it most likely came from:</p>

<ul>
	<li>📚 <strong>BOOK:</strong> A comprehensive non-fiction work or textbook.</li>
	<li>🔬 <strong>PEER-REVIEWED JOURNAL:</strong> Original academic research, highly specialized.</li>
	<li>📰 <strong>NEWSPAPER ARTICLE:</strong> Timely reports on current events, official statements, or broad trends.</li>
	<li>▶️ <strong>VIDEO:</strong> Documentaries, expert lectures, news reports, or interviews captured visually.</li>
	<li>🗣️ <strong>INTERVIEW:</strong> Direct quotes or personal observations from an expert or witness.</li>
</ul>

<p>Your <strong>Credibility Meter</strong> is paramount &ndash; it reflects how trustworthy your report is! Let&#39;s get started!</p>
<button class="game-button" id="start-button">Start Game</button></div>

<div id="game-area" style="display: none;">
<h2>Research Question: <span id="research-question">What are the major environmental impacts of plastic pollution?</span></h2>

<div id="credibility-section">Credibility: <span id="credibility-score">0</span> / <span id="max-credibility"></span>

<div id="credibility-bar-container">
<div id="credibility-bar">&nbsp;</div>
</div>
</div>

<div id="snippet-card">
<p id="current-snippet-text">Loading...</p>
</div>

<div id="source-cards"><button class="source-button" data-source-type="Book"><span class="icon">📚</span> BOOK</button><button class="source-button" data-source-type="Peer-Reviewed Journal"><span class="icon">🔬</span> PEER-REVIEWED JOURNAL</button><button class="source-button" data-source-type="Newspaper Article"><span class="icon">📰</span> NEWSPAPER ARTICLE</button><button class="source-button" data-source-type="Video"><span class="icon">▶️</span> VIDEO</button><button class="source-button" data-source-type="Interview"><span class="icon">🗣️</span> INTERVIEW</button></div>

<div id="feedback">&nbsp;</div>

<div id="report-section">
<h3>Your Report:</h3>

<ul id="report-list">
</ul>
</div>
</div>

<div id="game-end-screen" style="display: none;">
<p>Game Over!</p>

<p>Your Final Credibility Score: <span class="summary-score" id="final-score"></span> / <span id="max-credibility-end"></span></p>

<p class="summary-message" id="end-message">&nbsp;</p>
<button class="game-button" id="reset-button">Play Again</button></div>
</div>
<script>
        // --- Game Data (Snippets and their correct sources) ---
        const gameData = [
            {
                text: "Globally, an estimated 8 million metric tons of plastic waste enter our oceans each year, equivalent to dumping a garbage truck of plastic into the ocean every minute.",
                correctSource: "Peer-Reviewed Journal",
                isMisinformation: false,
                explanation: "Specific, large-scale statistics like this typically come from rigorous scientific studies."
            },
            {
                text: "In a recent city council meeting, Mayor Thompson stated, 'We are committed to reducing single-use plastics in our community and are exploring new recycling initiatives.'",
                correctSource: "Newspaper Article",
                isMisinformation: false,
                explanation: "Direct quotes from public officials at public meetings are usually reported in newspapers for public information."
            },
            {
                text: "Marine animals, such as sea turtles and birds, frequently mistake plastic debris for food, leading to internal injuries, starvation, and even death.",
                correctSource: "Book",
                isMisinformation: false,
                explanation: "General scientific facts and well-established impacts are often compiled and explained in comprehensive books."
            },
            {
                text: "I've seen firsthand the devastating effects of microplastics. During my last dive in the Pacific, I pulled out a plastic bag filled with thousands of tiny plastic fragments that had been ingested by plankton.",
                correctSource: "Interview",
                isMisinformation: false,
                explanation: "Personal observations and anecdotes, even from experts, are characteristic of interview data."
            },
            {
                text: "New research indicates that microplastics can act as carriers for harmful chemicals and pathogens, potentially transferring them up the food chain to humans.",
                correctSource: "Peer-Reviewed Journal",
                isMisinformation: false,
                explanation: "The phrase 'new research indicates' points directly to original scientific findings, usually found in peer-reviewed journals."
            },
            {
                text: "Plastic pollution is a hoax created by the paper industry to boost sales of paper bags.",
                correctSource: "None (Misinformation)",
                isMisinformation: true,
                explanation: "This is a baseless claim. Misinformation often lacks credible sources and may contradict established scientific consensus."
            },
            {
                text: "A recent documentary on ocean health showed time-lapse footage of a plastic bottle breaking down into microplastics over several years, highlighting the long-term persistence of plastic debris.",
                correctSource: "Video",
                isMisinformation: false,
                explanation: "Visual evidence, especially time-lapse footage, is a key characteristic of video content like documentaries."
            },
            {
                text: "Professor Anya Sharma, a leading environmental scientist, stated in a recent public lecture that 'Reducing our plastic footprint requires systemic changes, not just individual efforts.'",
                correctSource: "Video", // Could also be Interview if transcribed, but lecture implies video
                isMisinformation: false,
                explanation: "Quotes from public lectures are typically captured and shared via video recordings."
            },
            {
                text: "The 'Great Pacific Garbage Patch' is not a solid island of trash, but rather a vast area of dispersed plastic particles, microplastics, and larger debris.",
                correctSource: "Book",
                isMisinformation: false,
                explanation: "Clarifying common misconceptions and providing comprehensive context is often found in educational books."
            },
            {
                text: "A 2023 study published in *Nature Geoscience* found that plastic pollution is contributing to the warming of the atmosphere by releasing greenhouse gases as it degrades.",
                correctSource: "Peer-Reviewed Journal",
                isMisinformation: false,
                explanation: "Specific journal names and findings from recent, high-impact studies are definitively found in peer-reviewed journals."
            },
            {
                text: "During my cleanup efforts, I found a 30-year-old plastic bottle with the original soda branding still visible, showing how incredibly durable these materials are.",
                correctSource: "Interview",
                isMisinformation: false,
                explanation: "This is a personal observation and experience from someone involved in the field, typical of an interview."
            }
        ];

        // --- Game State Variables ---
        let credibilityScore = 0;
        let maxCredibility = 0;
        let currentSnippetIndex = 0;
        let shuffledGameData = [];
        const maxScorePerCorrect = 10;
        const penaltyIncorrect = -5;
        const penaltyMisinformation = -15;
        const passingScore = 70; // Percentage of maxCredibility to "pass"

        // --- DOM Elements ---
        const gameIntro = document.getElementById('game-intro');
        const gameArea = document.getElementById('game-area');
        const gameEndScreen = document.getElementById('game-end-screen');

        const startButton = document.getElementById('start-button');
        const resetButton = document.getElementById('reset-button');

        const credibilityScoreElem = document.getElementById('credibility-score');
        const maxCredibilityElem = document.getElementById('max-credibility');
        const credibilityBar = document.getElementById('credibility-bar');
        const currentSnippetTextElem = document.getElementById('current-snippet-text');
        const sourceButtons = document.querySelectorAll('.source-button');
        const feedbackElem = document.getElementById('feedback');
        const reportList = document.getElementById('report-list');

        const finalScoreElem = document.getElementById('final-score');
        const maxCredibilityEndElem = document.getElementById('max-credibility-end');
        const endMessageElem = document.getElementById('end-message');

        // --- Game Initialization ---
        document.addEventListener('DOMContentLoaded', initGame);

        function initGame() {
            // Calculate max possible credibility
            maxCredibility = gameData.filter(s => !s.isMisinformation).length * maxScorePerCorrect;
            maxCredibilityElem.textContent = maxCredibility;
            maxCredibilityEndElem.textContent = maxCredibility; // For end screen

            // Set initial state
            credibilityScore = 0;
            currentSnippetIndex = 0;
            updateCredibilityDisplay();
            reportList.innerHTML = ''; // Clear previous report

            gameIntro.style.display = 'block';
            gameArea.style.display = 'none';
            gameEndScreen.style.display = 'none';
            resetButton.style.display = 'none'; // Only show at end
            startButton.style.display = 'block'; // Ensure start button is visible

            // Add event listeners
            startButton.addEventListener('click', startGame);
            resetButton.addEventListener('click', initGame); // Reset on play again

            sourceButtons.forEach(button => {
                button.addEventListener('click', () => handleSourceClick(button.dataset.sourceType));
                button.disabled = true; // Disable until game starts
            });
        }

        // --- Game Start ---
        function startGame() {
            gameIntro.style.display = 'none';
            gameArea.style.display = 'block';
            resetButton.style.display = 'none'; // Hide if somehow visible

            // Shuffle game data for replayability
            shuffledGameData = [...gameData].sort(() => Math.random() - 0.5);

            displayNextSnippet();
        }

        // --- Display Snippets ---
        function displayNextSnippet() {
            feedbackElem.textContent = '';
            feedbackElem.className = ''; // Clear feedback styling

            if (currentSnippetIndex < shuffledGameData.length) {
                const currentSnippet = shuffledGameData[currentSnippetIndex];
                currentSnippetTextElem.textContent = currentSnippet.text;
                sourceButtons.forEach(button => button.disabled = false); // Enable source buttons
            } else {
                endGame(); // All snippets processed
            }
        }

        // --- Handle User Source Selection ---
        function handleSourceClick(selectedSource) {
            sourceButtons.forEach(button => button.disabled = true); // Disable buttons while processing

            const currentSnippet = shuffledGameData[currentSnippetIndex];
            let feedbackMessage = '';
            let feedbackClass = '';
            let reportStatusIcon = '';
            let reportStatusClass = '';

            if (currentSnippet.isMisinformation) {
                credibilityScore += penaltyMisinformation;
                feedbackMessage = `❌ DISCREDITED INFORMATION! "${currentSnippet.text}" is false or unreliable. Avoid using such claims in a credible report. (Penalty: ${penaltyMisinformation} points)`;
                feedbackClass = 'feedback-misinformation';
                reportStatusIcon = '❌';
                reportStatusClass = 'status-discredited';
                // Don't add misinformation to the main report list
            } else {
                if (selectedSource === currentSnippet.correctSource) {
                    credibilityScore += maxScorePerCorrect;
                    feedbackMessage = `✅ Correct! "${currentSnippet.text}" is best sourced from a ${currentSnippet.correctSource}. (Score: +${maxScorePerCorrect} points)`;
                    feedbackClass = 'feedback-correct';
                    reportStatusIcon = '✅';
                    reportStatusClass = 'status-correct';
                    addSnippetToReport(currentSnippet.text, currentSnippet.correctSource, true);
                } else {
                    credibilityScore += penaltyIncorrect;
                    feedbackMessage = `⚠️ Not quite. "${currentSnippet.text}" is good information, but without the correct source (${currentSnippet.correctSource}), its trustworthiness is reduced. (Penalty: ${penaltyIncorrect} points)`;
                    feedbackClass = 'feedback-incorrect';
                    reportStatusIcon = '⚠️';
                    reportStatusClass = 'status-uncited';
                    addSnippetToReport(currentSnippet.text, currentSnippet.correctSource, false);
                }
            }

            feedbackElem.textContent = feedbackMessage;
            feedbackElem.className = feedbackClass; // Apply class for styling

            updateCredibilityDisplay();

            currentSnippetIndex++; // Move to next snippet
            setTimeout(displayNextSnippet, 3000); // Show feedback for 3 seconds before next snippet
        }

        // --- Update Credibility Display ---
        function updateCredibilityDisplay() {
            credibilityScore = Math.max(0, credibilityScore); // Ensure score doesn't go below 0
            credibilityScoreElem.textContent = credibilityScore;
            const barWidth = (credibilityScore / maxCredibility) * 100;
            credibilityBar.style.width = `${barWidth}%`;

            if (credibilityScore < (maxCredibility * 0.3)) { // Low score warning
                credibilityBar.style.backgroundColor = '#dc3545'; // Red
            } else if (credibilityScore < (maxCredibility * 0.6)) { // Medium score
                credibilityBar.style.backgroundColor = '#ffc107'; // Orange
            } else { // High score
                credibilityBar.style.backgroundColor = '#28a745'; // Green
            }
        }

        // --- Add Snippet to Report ---
        function addSnippetToReport(text, correctSource, isCorrectlyCited) {
            const listItem = document.createElement('li');
            let statusText = '';
            let statusIcon = '';
            let statusClass = '';

            if (isCorrectlyCited) {
                statusText = `(Source: ${correctSource})`;
                statusIcon = '✅';
                statusClass = 'status-correct';
            } else {
                statusText = `(UNCITED - Best Source: ${correctSource})`;
                statusIcon = '⚠️';
                statusClass = 'status-uncited';
            }

            listItem.innerHTML = `<span class="status-icon ${statusClass}">${statusIcon}</span> ${text} <br> <em>${statusText}</em>`;
            reportList.appendChild(listItem);
            reportList.scrollTop = reportList.scrollHeight; // Scroll to bottom
        }

        // --- End Game ---
        function endGame() {
            gameArea.style.display = 'none';
            gameEndScreen.style.display = 'block';
            resetButton.style.display = 'block'; // Show play again button

            finalScoreElem.textContent = credibilityScore;

            let message = "";
            const scorePercentage = (credibilityScore / maxCredibility) * 100;

            if (scorePercentage >= 90) {
                message = "Outstanding! Your report is highly credible and well-sourced. You're a true Truth Threader!";
            } else if (scorePercentage >= passingScore) {
                message = "Great job! Your report is credible, but there's always room to refine your sourcing skills.";
            } else if (scorePercentage >= 30) {
                message = "Good effort, but your report's credibility is a bit low. Remember to always cite and be wary of misinformation!";
            } else {
                message = "Your report lacks credibility. Review the importance of sources and try again. Don't let misinformation slip through!";
            }
            endMessageElem.textContent = message;
        }

    </script>
