<script>
    import { onMount } from 'svelte';
    let audioElement, hiddenSection, moreInfo, revealButton;

    function playAudio() {
        audioElement?.play();
        if (hiddenSection) {
            hiddenSection.classList.remove('hidden');
            hiddenSection.scrollIntoView({ behavior: 'smooth', block: 'center' });
        }
    }

    function toggleMoreInfo() {
        if (moreInfo) {
            moreInfo.classList.toggle('hidden');
            revealButton.textContent = moreInfo.classList.contains('hidden') ? 'Click to reveal more' : 'Click to hide';
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

<main class="container">
    <button on:click={playAudio}>Click to know me</button>
    <h2>Mute audio if you don't want sound!</h2>
</main>

<audio id="background-music" loop>
    <source src="/Call of Duty Black Ops Multiplayer Menu Music (mp3cut.net).mp3" type="audio/mpeg">
</audio>

<section id="hidden-section" class="hidden">
    <header>
        <h2>Hello Soldier, My name is Ruben Erhardt.</h2>
    </header>
    <p class="classified">CLASSIFIED</p>
    <button id="reveal-button">Click to reveal more</button>
    <div id="more-info" class="hidden">
        <article class="info-container">
            <a href="https://github.com/RubenErhardt">
                <img src="/Squad2C-Ruben.JPG" alt="Mugshot of Ruben Erhardt" width="100" height="150" loading="lazy">
            </a>
            <section class="skills-list">
                <h3>My skills are:</h3>
                <ol>
                    <li>HTML</li>
                    <li>CSS</li>
                    <li>JavaScript</li>
                </ol>
            </section>
            <section class="hobby-list">
                <h3>My hobbies are:</h3>
                <ol>
                    <li>Gaming</li>
                    <li>Dogs</li>
                    <li>Beers</li>
                </ol>
            </section>
        </article>
    </div>
</section>

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
    border-radius: 10px;
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
    transform: scale(1.1);
}

button:active {
    transform: scale(0.95);
}

h2 {
    font-size: 18px;
    color: #ffffff;
    text-align: center;
}

.hidden {
    display: none;
}


#hidden-section {
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
    overflow: hidden;
    border-right: .15em solid orange;
    white-space: nowrap;
    margin: 0 auto;
    letter-spacing: .15em;
    animation: typing 3.5s steps(30, end), blink-caret .5s step-end infinite;
}

@keyframes typing {
    from { width: 0 }
    to { width: 100% }
}

@keyframes blink-caret {
    from, to { border-color: transparent }
    50% { border-color: orange }
}

.classified {
    font-size: 80px;
    color: rgba(239, 8, 8, 0.5);
    transform: rotate(-15deg) translateX(10px) translateY(10px);
}

#more-info {
    margin-top: 20px;
}

.info-container {
    display: flex;
    align-items: center;
    gap: 20px;
}

.info-container img {
    border-radius: 8px;
    filter: grayscale(80%);
    box-shadow: 0 0 10px 2px rgba(255, 165, 0, 0.8);
    transition: box-shadow 0.3s ease;
    cursor: pointer;
}

.info-container img:hover {
    box-shadow: 0 0 15px 4px rgba(255, 165, 0, 1);
}

.skills-list, .hobby-list {
    text-align: left;
    color: white;
    margin-left: 40px;
    overflow: hidden;
    border-right: .15em solid orange;
    letter-spacing: .10em;
    animation: typing 3.5s steps(30, end), blink-caret .5s step-end infinite;
}

.skills-list h3, .hobby-list h3 {
    margin-bottom: 10px;
}

.skills-list ol, .hobby-list ol {
    margin: 0;
    padding-left: 20px;
}

@media only screen and (max-width: 1024px) {
    #hidden-section {
        width: 70%;
        margin-left: 50px;
        height: auto;
    }
    .info-container {
        flex-direction: column;
        gap: 10px;
    }
    .skills-list, .hobby-list {
        margin-left: 0;
        letter-spacing: .05em;
    }
}

@media only screen and (max-width: 768px) {
    #hidden-section {
        width: 90%;
        margin-left: 20px;
    }
    .info-container img {
        width: 80px;
        height: 120px;
    }
}

@media only screen and (max-width: 480px) {
    .container {
        height: auto;
        padding: 20px;
    }
    button {
        padding: 10px 30px;
        font-size: 18px;
    }
    #hidden-section {
        width: 100%;
        margin-left: 0;
        padding: 15px;
    }

    #hidden-section h2 {
        font-size: 14px;
    }

    .classified {
        font-size: 50px;
    }
    .skills-list, .hobby-list {
        letter-spacing: .03em;
    }
}
</style>
