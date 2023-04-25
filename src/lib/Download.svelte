<script>
    import playstorenormal from "../assets/playstore.png";
    import playstoregray from "../assets/playstoregray.png";
    import applenormal from "../assets/apple.png";
    import applegray from "../assets/applegray.png";
    let playstore = playstoregray;
    function hMIg(e) {
        playstore = playstorenormal;
    }
    function hMOg(e) {
        playstore = playstoregray;
    }
    let apple = applegray;
    function hMIa(e) {
        apple = applenormal;
    }
    function hMOa(e) {
        apple = applegray;
    }
</script>

<h1>Download Safety service now</h1>
<img
    id="google"
    on:mouseover={hMIg}
    on:mouseout={hMOg}
    src={playstore}
    alt=""
/>
<img id="apple" on:mouseover={hMIa} on:mouseout={hMOa} src={apple} alt="" />

<style>
    img {
        position: absolute;
        width: 23vh;
        top: 65vh;
    }
    #apple {
        right: 15vw;
    }
    #google {
        left: 15vw;
    }
    @media screen and (max-width: 650px) {
        h1 {
            text-align: center;
        }
        img {
            width: 13vh;
        }
    }
</style>
