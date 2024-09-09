<script>
    import { onMount } from 'svelte';
    let audioElement;
    let hiddenSection;
    let moreInfo;
    let revealButton;

    function playAudio() {
        if (audioElement) {
            audioElement.play();
        }
        if (hiddenSection) {
            hiddenSection.style.display = 'block';
            hiddenSection.style.opacity = 1; 
            hiddenSection.scrollIntoView({ behavior: 'smooth', block: 'center' });

            // Remove scrollbars
            document.body.style.overflow = 'hidden';
        }
    }

    function toggleMoreInfo() {
        if (moreInfo) {
            // Toggle visibility of more info
            moreInfo.classList.toggle('hidden');
            // Change button text depending on visibility
            if (moreInfo.classList.contains('hidden')) {
                revealButton.textContent = 'Click to reveal more';
            } else {
                revealButton.textContent = 'Click to hide';
            }
        }
    }

    onMount(() => {
        audioElement = document.getElementById('background-music');
        hiddenSection = document.getElementById('hidden-section');
        moreInfo = document.getElementById('more-info');
        revealButton = document.getElementById('reveal-button');
        revealButton.addEventListener('click', toggleMoreInfo);
    });
</script>

<div class="container">
    <button on:click={playAudio}>Click to know me</button>
    <h2>Mute audio if you don't want sound!</h2>
</div>

<audio id="background-music" loop>
    <source src="/[1080p HD] Call of Duty Black Ops Multiplayer Menu Music (mp3cut.net).mp3" type="audio/mpeg">
</audio>

<!-- Hidden section -->
<div id="hidden-section" class="hidden">
    <h2>Hello Soldier, My name is Ruben Erhardt.</h2>
    <p class="classified">CLASSIFIED</p>
    <button id="reveal-button">Click to reveal more</button>
    <div id="more-info" class="hidden">
        <div class="info-container">
            <img src="/Squad2C-Ruben.JPG" alt="Mugshot of Ruben Erhardt" width="100" height="150">
            <div class="skills-list">
                <p>My skills are:</p>
                <ol>
                    <li>HTML</li>
                    <li>CSS</li>
                    <li>JavaScript</li>
                </ol>
            </div>
        </div>
    </div>
</div>

<style>
    .container {
        display: flex;
        flex-direction: column; 
        align-items: center; 
        justify-content: center; 
        height: 100vh; 
    }

    button {
        padding: 15px 40px;
        font-size: 20px;
        font-weight: bold;
        color: black;
        background: linear-gradient(135deg, #f08d03, #ee6d04);
        border: none;
        box-shadow: 0 10px 15px rgba(0, 0, 0, 0.4);
        cursor: pointer;
        transition: all 0.4s ease;
        position: relative;
    }

    button:hover {
        transform: scale(1.1); /* Slightly increase size */
    }

    button:active {
        transform: scale(0.95); /* Shrink on click */
    }

    h2 {
        font-size: 18px;
        color: #ffffff;
        text-align: center;
    }

    /* Hidden section styling */
    #hidden-section {
        display: none; /* Hide initially */
        max-width: 500px;
        width: 30%;
        height: 500px;
        padding: 20px;
        margin-left: 100px;
        box-shadow: 1px 3px 3px 3px rgba(232, 137, 3, 0.925);
        color: black;
        text-align: center;
        margin-bottom: 100px;
        border-radius: 8px;
        background-color: rgba(53, 50, 50, 0.4);
    }

    #hidden-section h2 {
        color: #000000;
        background-color: white;
        font-size: 18px;
        overflow: hidden; /* Ensures the content is not revealed until the animation */
        border-right: .15em solid orange; /* The typewriter cursor */
        white-space: nowrap; /* Keeps the content on a single line */
        margin: 0 auto; /* Gives that scrolling effect as the typing happens */
        letter-spacing: .15em; /* Adjust as needed */
        animation: 
            typing 3.5s steps(30, end),
            blink-caret .5s step-end infinite;
    }

    /* The typing effect */
    @keyframes typing {
        from { width: 0 }
        to { width: 100% }
    }

    /* The typewriter cursor effect */
    @keyframes blink-caret {
        from, to { border-color: transparent }
        50% { border-color: orange }
    }

    .classified {
        font-size: 80px;
        color: rgba(239, 8, 8, 0.5);
        transform: rotate(-15deg) translateX(10px) translateY(10px); /* Combined rotation and translation */
    }

    .hidden {
        display: none;
    }

    .hidden button {
        font-size: 15px;
    }

    #more-info {
        margin-top: 20px; /* Space above the additional text */
    }

    .info-container {
        display: flex; /* Align items horizontally */
        align-items: center; /* Vertically center items */
        gap: 20px; /* Space between the items */
    }

    .info-container img {
    border-radius: 8px; /* Optional styling for rounded corners */
    filter: grayscale(80%); /* Convert image to black and white */
    box-shadow: 0 0 10px 2px rgba(255, 165, 0, 0.8); /* Orange glow effect */
    transition: box-shadow 0.3s ease; /* Smooth transition for hover effect */
    cursor: pointer;
}

.info-container img:hover {
    box-shadow: 0 0 15px 4px rgba(255, 165, 0, 1); /* Enhanced glow effect on hover */
}

    .skills-list {
        text-align: left; /* Align text to the left in the skills list */
        color: white;
    }

    .skills-list p {
        margin: 0 0 10px 0; /* Space below the paragraph */
    }

    .skills-list ol {
        margin: 0; /* Remove default margin */
        padding-left: 20px; /* Space for list markers */
    }
</style>
