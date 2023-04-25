<script>
    import emailjs from "@emailjs/browser";
    let email = "";
    let email_count = 3;
    let own_question = "";
    let all = [
        {
            question: "How does Safety service actually work?",
            answer: 'When the app hears "Kay" it activates the state "unsafe" after hearing: "unsafe", "help", "save me", "help me", "leave me alone" your chosen contact will be notified, other safe words can be chosen.',
            open: false,
        },
        {
            question: "Do you need a Wifi connection?",
            answer: "No, you you don't need a connection activate the `unsafe` mode.",
            open: false,
        },
        {
            question: "Can I specify my contact who I notify?",
            answer: "Yes, it's in the app settings.",
            open: false,
        },
        {
            question: "How can I add the Police to my contacts?",
            answer: "Yes, the police is automatically informed of your situation.",
            open: false,
        },
    ];
    function sendEmail(e) {
        if (email_count == 0) {
            return;
        }
        emailjs
            .sendForm(
                "service_pf6hwvo",
                "template_wzo74j8",
                "from" + email + " : " + e.target,
                "QStSXdhyGYJpysro2"
            )
            .then(
                (result) => {
                    console.log("SUCCESS!", result.text);
                },
                (error) => {
                    console.log("FAILED...", error.text);
                }
            );
        own_question = "";
        email = "";
        email_count -= 1;
    }
    const open = (i) => {
        all[i].open = !all[i].open;
    };
</script>

<h1>FAQ</h1>

<div class="questions">
    {#each all as item, i}
        <div class="question">
            <h3 class="title">{item.question}</h3>
            {#if item.open}
                <p class="answer">{item.answer}</p>
            {/if}
            <button on:click={() => open(i)}>
                {#if item.open}
                    ⬆️
                {:else}
                    ⬇️
                {/if}
            </button>
        </div>
    {/each}
</div>
<div class="own-questions-div">
    <h3>If you have any questions left mail them.</h3>
    <form on:submit|preventDefault={sendEmail}>
        <label>Email</label>
        <input type="email" name="user_email" />
        <label>Message</label>
        <textarea name="message" />
        <button type="submit"> Send </button>
    </form>
</div>

<style>
    @media screen and (min-width: 650px) {
        .question {
            background: #65a1ac;
            border-radius: 12px;
            width: calc(40% + 10vh);
            padding: 1.5vh;
            margin: 1vh;
            display: flex;
            flex-direction: column;
            flex-basis: 100%;
            flex: 1;
        }
        .question button {
            border: 0;

            width: 3.5vh;
            height: 3.5vh;
            border-radius: 12px;
            background: #45717c;
        }
        .own-questions-div {
            background: orange;
            width: 44%;
            padding: 2vh;
            margin: 1vh;
            border-radius: 12px;
            position: absolute;
            right: -1%;
            top: 21.5%;
        }
        .own-questions-div * {
            padding: 1vh;
            margin: 0.2vh;
        }

        .own-questions-div form textarea,
        form input {
            width: 94%;
        }
    }
    @media screen and (max-width: 650px) {
        .question {
            background: #65a1ac;
            padding: 0.5vw;
            margin-top: 1.5vw;
            margin-right: 5%;
            margin-left: 1%;

            border-radius: 12px;
        }
        .question p {
            padding: 1vh;
        }
        .own-questions-div {
            background: orange;
            padding: 2vh;
            margin: 1vh;
            border-radius: 12px;
            margin-top: 1.5vw;
            margin-right: 5%;
            margin-left: 1%;
        }
        .own-questions-div form textarea,
        form input {
            padding: 1vh;
            margin: 0.2vh;
            width: 94%;
        }
    }
</style>
