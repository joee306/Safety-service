<h1>Safety service</h1>
<p class="description">
    This App will be the future of public safety! It will allow you to quickly
    share your location with your friends and family as soon as you feel unsafe.
    For better safety measurements the police and other government forces will
    be able to see you location over GPS. Informs your chosen contacts of your
    whereabouts
</p>
<div class="show">
    <img
        src="https://media.discordapp.net/attachments/953532690957729803/1100045660994146404/IMG_9458.png?width=371&height=660"
        alt=""
    />
</div>

<style>
    :global(h1) {
        margin-top: 10vh;
    }
    .description,
    .show {
        background: #65a1ac;
        border-radius: 12px;
    }
    .description {
        width: calc(40% + 10vh);
        padding: 20px;
    }
    @media screen and (min-width: 650px) {
        .show {
            top: 35%;
            right: calc(3vh + 2%);
            transform: rotate(7deg);
            padding: 8px;
            position: absolute;
        }
        .show img {
            width: 12vw;
        }
    }
    @media screen and (max-width: 650px) {
        .show {
            margin-top: 30%;
            left: 50%;
            transform: translateX(60%);
            padding: 8px;
            width: 40%;
        }
        .show img {
            width: 100%;
        }
        .description {
            width: 85%;
        }
        h1 {
            text-align: center;
        }
    }
</style>
