<template>

    <div class="uk-section-primary tm-section">

        <navbar class="uk-navbar-transparent"></navbar>

        <div class="uk-section uk-flex uk-flex-middle uk-text-center" uk-height-viewport="offset-top: true">
            <div class="uk-width-1-1">
                <div class="uk-container">

                    <p class="uk-margin-large-bottom">
                        <img :src="'./images/download.svg'">
                    </p>

                    <h1>Thanks for giving UIkitty a try.</h1>

                    <p class="uk-margin-medium-bottom uk-text-large">Please support our open source project and share the love on<br class="uk-visible@s"> Twitter or Facebook. It would really mean a lot to us.</p>

                    <div class="uk-grid-medium uk-child-width-auto uk-flex-inline" uk-grid>
                        <div>
                            <a class="uk-button uk-button-primary tm-button-primary uk-button-large" href="https://twitter.com/intent/tweet?text=I'm+excited+to+try+@uikitty1,+a+modern+front-end+framework.+Check+it+out+at+https%3a%2f%uikitty.com" target="_blank">
                                <span class="uk-margin-small-right" uk-icon="icon: twitter"></span>
                                <span class="uk-text-middle">Share on Twitter</span>
                            </a>
                        </div>
                        <div>
                            <a class="uk-button uk-button-primary tm-button-primary uk-button-large" href="https://www.facebook.com/sharer/sharer.php?u=https://uikitty.com" target="_blank">
                                <span class="uk-margin-small-right" uk-icon="icon: facebook"></span>
                                <span class="uk-text-middle">Post on Facebook</span>
                            </a>
                        </div>
                    </div>

                </div>
            </div>
        </div>

    </div>

</template>

<script>

    import $ from 'jquery';

    export default {

        mounted() {

            $.get("assets/uikit/package.json", {nocache: Math.random()}, data => {
                setTimeout(() => {
                    location.href = `https://github.com/qodeone/uikitty3/archive/8.x-3.4.zip`;
                }, 100);
            }, 'json');

        }
    }

</script>
