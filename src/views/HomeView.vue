<script lang="ts">
import BaseButton from "@/components/BaseButton.vue";
import { defineComponent } from "vue";

export default defineComponent({
    components: { BaseButton },
    setup() {
        const onClick = (e: Event) => {
            console.log(e);
        };

        return { onClick };
    }
});
</script>

<template>
    <main>
        <h1>Bartłomiej Nowak - zadanie rekrutacyjne</h1>
        <div class="margin-top">
            <div class="margin-right">Normalne przyciski:</div>
            <base-button color="dark-orange" class="margin-right">Text</base-button>
            <base-button color="orange" class="margin-right">Other text</base-button>
            <base-button color="green" class="margin-right">Click here</base-button>
            <base-button color="dark-green" class="margin-right">Wybierz teraz</base-button>
            <base-button color="red" class="margin-right">Anuluj wizytę</base-button>
        </div>

        <div class="margin-top">
            <div class="margin-right">Przyciski w stylu outlined:</div>
            <base-button color="dark-orange" outlined class="margin-right">Text</base-button>
            <base-button color="orange" outlined class="margin-right">Other text</base-button>
            <base-button color="green" outlined class="margin-right">Click here</base-button>
            <base-button color="dark-green" outlined class="margin-right"
                >Wybierz teraz</base-button
            >
            <base-button color="red" outlined class="margin-right">Anuluj wizytę</base-button>
        </div>

        <div class="margin-top">
            <div class="margin-right">Zablokowane przyciski:</div>
            <base-button color="dark-orange" disabled class="margin-right">Text</base-button>
            <base-button color="orange" disabled class="margin-right">Other text</base-button>
            <base-button color="green" disabled class="margin-right">Click here</base-button>
            <base-button color="dark-green" disabled class="margin-right"
                >Wybierz teraz</base-button
            >
            <base-button color="red" disabled class="margin-right">Anuluj wizytę</base-button>
        </div>

        <div class="margin-top">
            <div class="margin-right">Zablokowane przyciski w stylu outlined:</div>
            <base-button color="dark-orange" disabled outlined class="margin-right"
                >Text</base-button
            >
            <base-button color="orange" disabled outlined class="margin-right"
                >Other text</base-button
            >
            <base-button color="green" disabled outlined class="margin-right"
                >Click here</base-button
            >
            <base-button color="dark-green" disabled outlined class="margin-right"
                >Wybierz teraz</base-button
            >
            <base-button color="red" disabled outlined class="margin-right"
                >Anuluj wizytę</base-button
            >
        </div>

        <div class="margin-top">
            <div class="margin-right">Przyciski różnych rozmiarów:</div>
            <base-button color="dark-orange" size="small" class="margin-right">Text</base-button>
            <base-button color="orange" size="small" class="margin-right">Other text</base-button>
            <base-button color="green" class="margin-right">Click here</base-button>
            <base-button color="dark-green" size="large" class="margin-right"
                >Wybierz teraz</base-button
            >
            <base-button color="red" size="large" class="margin-right">Anuluj wizytę</base-button>
        </div>
        <div class="margin-top">
            <div>Przycisk a:</div>
            <base-button :component="{ type: 'a', address: 'https://risify.pl' }"
                >Risify</base-button
            >
        </div>
        <div class="margin-top">
            <div>Przycisk router-link:</div>
            <base-button :component="{ type: 'router-link', address: 'lorem-ipsum' }"
                >Lorem ipsum</base-button
            >
        </div>
        <div class="margin-top">
            <div>Przycisk z obsługiwanym eventem:</div>
            <base-button @click="onClick">Lorem ipsum</base-button>
        </div>
        <div class="margin-top">
            <div>Przycisk ze zdjęciem:</div>
            <base-button
                ><img
                    class="img"
                    src="../assets/img/lego-jeż.jpg"
                    alt=""
                    style="height: 50px"
                /><img
                    class="img"
                    src="../assets/img/lego-jeż.jpg"
                    alt=""
                    style="height: 50px"
                />Jeż</base-button
            >
        </div>
        <div class="margin-top">
            <div>Przycisk block:</div>
            <div style="width: 250px; height: 250px">
                <base-button blockDisplay>Block</base-button>
            </div>
        </div>
    </main>
</template>

<style scoped lang="scss">
main {
    margin: 1rem;
}

.img {
    height: 50x;
}
</style>
