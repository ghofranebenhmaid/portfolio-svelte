<style lang="scss" global>
@import "../styles/globals.scss";
@import "../styles/footer.scss";

:global(body.dark-mode) .borderTop {
    border-top: 0.5px solid var(--color-primary);
}
</style>

<script>
import SocialMediaAccounts from "../components/SocialMediaAccounts.svelte"
</script>

<div class="footer">
    <div class="container">
        <div class="borderTop"></div>
        <div class="footer__centent">
            <p>&copy; <em>{new Date().getFullYear()}</em> Ghofrane Ben Hmaid</p>
            <SocialMediaAccounts />
        </div>
    </div>
</div>
