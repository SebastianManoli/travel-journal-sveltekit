<script>
    let email = "";
    let password = "";
    let confirmPassword = "";
    let error = false;
    let register = false;

    function handleAuthenticate(){
        if (!email || !password || !confirmPassword) {
            error = true;
            return;
        }
    }

    function handleRegister(){
        register = !register;
    }

</script>


<div class="mainContainer">
    <div class="overlay"></div>
    <div class="authContainer">
        <form>
            <h1>{register ? "Register" : "Login"}</h1>

            {#if error}
                <p class="error">The information you have entered is incorrect</p>
            {/if}

            <label>
                <p class={email ? " above" :"  center"}>Email</p>
                <input 
                    bind:value={email} 
                    type="email" 
                    placeholder="Email"
                />
            </label>

            <label>
                <p class={password ? " above" : " center"}>Password</p>
                <input 
                    bind:value={password} 
                    type="password" 
                    placeholder="Password" 
                />
            </label>

            {#if register}
                <label>
                    <p class={confirmPassword ? " above" : " center"}>
                        Confirm Password
                    </p>
                    <input
                        bind:value={confirmPassword} 
                        type="password" 
                        placeholder="Confirm Password" 
                    />
                </label>
            {/if}

            <button type="submit">Submit</button>
        </form>
        <div class="options">
            <p>Or</p>
            {#if register}
                <div>
                    <p>Already have an account?</p>
                    <button on:click={handleRegister} on:keydown={()=>{}}>
                        Login
                    </button>
                </div>
            {:else}
                <div>
                    <p>Don't have an account?</p>
                    <button on:click={handleRegister} on:keydown={()=>{}}>
                        Register
                    </button>
                </div>
            {/if}
        </div>
    </div>
</div>

<style>
    .mainContainer {
        min-height: 100vh;
        color: white;
        position: relative;
        display: flex;
        flex-direction: column;

        /* Background image */
        background-image: url('/background-img-1.jpg');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
    }

    .overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100vh;
        background-color: black;
        opacity: 0.3;
        z-index: 0;
    }

    .authContainer {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        flex: 1;
        padding: 24px;
        z-index: 1;
    }
    
    h1 {
        text-align: center;
        font-size: 3rem;
        font-weight: 600;
    }

    form {
        display: flex;
        flex-direction: column;
        gap: 14px;
    }

    form,
    .options {
        width: 400px;
        max-width: 100%;
        margin: 0;
    }

    form input {
        width: 100%;
        border: none;
        background: transparent;
        color: white;
        padding: 14px;
        font-size: 1rem;
    }

    form input:focus {
        outline: none;
    }

    form label {
        position: relative;
        border: 1px solid white;
        border-radius: 5px;
    }

    form ::placeholder {
        color: #dceff8;
    }

    form button {
        border: none;
        color: white;
        padding: 10px 0;
        border: 1px solid white;
        border-radius: 20px;
        font-size: 1.2rem;
        font-weight: 600;
        cursor: pointer;
        background: transparent;
        border-color: white;
    }
    
    form button:hover {
        background-color: #71AEFE;
        color:white;
    }

    .above,
    .center {
        position: absolute;
        transform: translateY(-50%);
        pointer-events: none;
        color: black;
        border-radius: 4px;
        padding: 0 9px;
        font-size: 0.8rem;
    }

    .above {
        top: 0;
        left: 24px;
        background: white;
        border: solid 1px black;
        font-size: 0.7rem;
    }

    .center {
        top: 50%;
        left: 6px;
        border: solid 1px transparent;
        opacity: 0;
    }

    .error {
        color: red;
        font-size: 0.9rem;
    }

    .options {
        padding: 14px 0;
        overflow: hidden;
        font-size: 0.9rem;
        display: flex;
        flex-direction: column;
        gap: 8px;
    }

    .options > p {
        position: relative;
        text-align: center;
        width: fit-content;
        margin: 0 auto;
        padding: 0 8px;
    }

    .options > p::after,
    .options > p::before {
        position: absolute;
        content: "";
        top: 50%;
        transform: translateY(-50%);
        width: 100vw;
        height: 1.5px;
        background: white;
    }

    .options > p::after {
        right: 100%;
    }
    
    .options > p::before {
        left: 100%;
    }

    .options div {
        display: flex;
        align-items: center;
        gap: 8px;
        justify-content: center;
    }

    .options div button {
        cursor: pointer;
        text-decoration: underline;
        color: #3fbfff;
        background: none;
        border: none;
        font: inherit;
    }
</style>