<template>
    <div class="container">
        <div class="row">
            <div class="col-sm-12">
                <place-detail></place-detail>
            </div>
        </div>
    </div>
</template>

<script>
    import Place from './components/Place.vue';

    export default {
        components: {
            placeDetail: Place
        }
    }
</script>

<style>

</style>
