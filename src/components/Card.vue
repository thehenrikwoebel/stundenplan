<template>
    <v-card :title="fach" :color="getColor(fach)" width="20vw" height="12.5vh"></v-card>
</template>

<style scoped>

</style>

<script>
    export default {
        name: 'card',
        props: {
            fach: String,

        },
        data: () => ({
            getColor(fach) {
                switch (fach.toLowerCase()) {
                    case "mathe":
                        return "blue";
                        break;
                    case "deutsch":
                        return "red";
                        break;
                    case "englisch":
                        return "purple";
                        break;
                    case "informatik":
                        return "black";
                        break;
                    case "chemie":
                        return "yellow";
                        break;
                    case "frei":
                        return "white";
                        break;
                    case "physik":
                        return "green";
                        break;
                    case "erdkunde":
                        return "brown";
                        break;
                    case "geschichte":
                        return "grey";
                        break;
                    case "sport":
                        return "orange";
                        break;
                    default:
                        return "transparent"
                        break;
                }
            }
        }),
    }
</script>