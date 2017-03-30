<template>

    <div class="uk-section-primary tm-section">

        <navbar class="uk-navbar-transparent"></navbar>

        <div class="uk-section uk-section-small uk-flex uk-flex-middle uk-text-center" uk-height-viewport="offset-top: true; offset-bottom: true">
            <div class="uk-width-1-1">
                <div class="uk-container">

                    <p>
                        <img :src="'./images/uikitty-logo-large.svg'">
                    </p>

                    <p class="uk-margin-medium uk-text-lead">
                        A bridge between UIkit and Drupal 8. UIkitty is a lightweight and modular front-end framework<br class="uk-visible@s">
                        for developing faster, more powerful web interfaces on Drupal 8.
                    </p>

                    <div class="uk-child-width-auto uk-grid-medium uk-flex-inline uk-flex-center" uk-grid>
                        <div>
                            <a class="uk-button uk-button-primary tm-button-primary" href="./docs">3.x Documentation</a>
                        </div>
                        <div>
                            <a class="uk-button uk-button-default tm-button-default" href="https://github.com/qodeone/uikitty3">Github</a>
                        </div>
                        <div>
                            <a class="uk-button uk-button-default tm-button-default" href="https://drupal.org/uikitty3">Drupal.org</a>
                        </div>
                    </div>

                </div>
            </div>
        </div>

        <div class="uk-section-small">
            <div class="uk-container uk-container-expand uk-text-center uk-position-relative">

                <ul class="uk-subnav tm-subnav uk-flex-inline uk-flex-center uk-margin-remove-bottom" uk-margin>
                    <li>
                        Using the newest UIkit <span>Version <span uikit-version></span></span>
                    </li>

                    <li>
                        <a class="uk-text-lowercase" href="https://twitter.com/uikitty1"><span class="uk-margin-small-right" uk-icon="icon: twitter"></span>@uikitty1</a>
                    </li>
                </ul>

                <a class="uk-button uk-button-default tm-button-default uk-position-center-right uk-position-medium uk-visible@m" href="./v2">UIkitty 2.x <span uk-icon="icon: arrow-right"></span></a>

            </div>
        </div>

    </div>

</template>

<script>

    import $ from 'jquery';

    export default {

        mounted() {

            $.ajax({
                dataType : "jsonp",
                url      : "https://api.github.com/repos/uikit/uikit?callback=ukghapi&nocache="+Math.random(),
                success  : data => {

                    if (!data) return;

                    if (data.data.watchers){
                        $("[uikit-stargazers]").html(data.data.watchers);
                    }

                    if (data.data.forks){
                        $("[uikit-forks]").html(data.data.forks);
                    }
                }
            });

            $.get("assets/uikit/package.json", {nocache: Math.random()}, data => {
                $("[uikit-version]").text(data.version);
            }, 'json');

        }
    }

</script>
