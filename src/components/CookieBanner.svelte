<style>
.cookie-banner {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    padding: 10px;
    background-color: #f0f0f0;
    text-align: center;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

button {
    padding: 8px 16px;
    background-color: #4caf50;
    color: white;
    border: none;
    cursor: pointer;
}
</style>

<script>
let showBanner = true

function acceptCookies() {
    showBanner = false
    localStorage.setItem("cookiesAccepted", "true")
}
</script>

{#if showBanner}
    <div class="cookie-banner">
        <p>
            This website uses cookies to improve your experience. By using this site, you agree to
            our use of cookies.
        </p>
        <button on:click="{acceptCookies}">Accept</button>
    </div>
{/if}
