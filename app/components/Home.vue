<template>
    <Page class="page">
        <ActionBar class="action-bar">
            <Label class="action-bar-title" text="Home"></Label>
        </ActionBar>
        <ScrollView>
            <StackLayout class="home-panel">
                <Label horizontalAlignment="center" marginBottom="15" text="preferGoogleMaps set as True" />
                <Button marginBottom="15" text="Navigate without Way Points"
                    @tap="Navigate" />
                <Button text="Navigate with Way Points" @tap="NavigateWithPoints" />
            </StackLayout>
        </ScrollView>
    </Page>
</template>

<script>
    import { directions } from "../utils/map-directions"
    export default {
        methods: {
            Navigate() {
                directions
                    .navigate({
                        from: {
                            address: "Megaplaza"
                        },
                        to: {
                            address: "Plaza Norte"
                        },
                        type: "driving",
                        ios: {
                            preferGoogleMaps: true,
                            allowGoogleMapsWeb: true
                        }
                    })
                    .then(
                        () => {
                            console.log("Maps app launched.");
                        },
                        error => {
                            console.log(error);
                        }
                    );
            },
            NavigateWithPoints() {
                directions
                    .navigate({
                        from: {
                            address: "Megaplaza"
                        },
                        to: [{
                                address: "Plaza Norte"
                            },
                            {
                                address: "Royal Plaza"
                            }
                        ],
                        type: "driving",
                        ios: {
                            preferGoogleMaps: true,
                            allowGoogleMapsWeb: true
                        }
                    })
                    .then(
                        () => {
                            console.log("Maps app launched.");
                        },
                        error => {
                            console.log(error);
                        }
                    );
            }
        },
    };
</script>

<style scoped lang="scss">
    // Start custom common variables
    @import '../app-variables';
    // End custom common variables

    // Custom styles
    .fa {
        color: $accent-dark;
    }

    .info {
        font-size: 20;
    }
</style>
