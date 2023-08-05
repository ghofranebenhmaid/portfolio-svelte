<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/Home.scss";

.errorsvg {
    flex-direction: column;
}

:global(body) svg {
    fill: rgb(255, 255, 255);
}
:global(body.dark-mode) svg {
    fill: rgb(0, 0, 0);
}

:global(body) h4 {
    color: rgb(255, 255, 255);
}
:global(body.dark-mode) h4 {
    color: rgb(0, 0, 0);
}
.container-900 {
    height: calc(100vh - 297.09px);
}
</style>

<script>
import ErrorPage from "../components/ErrorPage.svelte"
</script>

<div class="container-900 errorsvg flex flex-jc-c flex-ai-c flex-jc-sa">
    <a data-sveltekit-reload href="/#/">
        <button class="flex flex-jc-c flex-ai-c">
            <h4>Back Home</h4>
            <svg
                xmlns="http://www.w3.org/2000/svg"
                width="30"
                height="30"
                viewBox="0 0 30 30"
                fill=""
                stroke="none"
                ><path
                    d="M1 15C0.447716 15 0 15.4477 0 16C0 16.5523 0.447716 17 1 17H24.254C22.9563 17.7179 21.7537 18.6189 20.6863 19.6863C17.9222 22.4504 16.2738 26.1218 16.0312 30.0005C15.9967 30.5517 16.4477 31 17 31C17.5523 31 17.9963 30.5517 18.0357 30.0008C18.2751 26.653 19.7115 23.4895 22.1005 21.1005C24.4895 18.7115 27.653 17.2751 31.0008 17.0357C31.5517 16.9963 32 16.5523 32 16C32 15.4477 31.5517 15.0037 31.0008 14.9643C27.653 14.7249 24.4895 13.2885 22.1005 10.8995C19.7115 8.51051 18.2751 5.34703 18.0357 1.99921C17.9963 1.44834 17.5523 1 17 1C16.4477 1 15.9967 1.44827 16.0312 1.99948C16.2738 5.8782 17.9222 9.54957 20.6863 12.3137C21.7537 13.3811 22.9563 14.2821 24.254 15H1Z"
                    fill=""></path></svg
            >
        </button>
    </a>
    <ErrorPage />
</div>
