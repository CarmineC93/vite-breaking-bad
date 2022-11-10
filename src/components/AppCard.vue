<script>
export default {
    name: "AppCard",
    props: {
        character: Object
    }
}
</script>

<template>
    <div class="character-card text-center">
        <img :src="character.img" :alt="character.name">
        <h4>{{ character.name }}</h4>
        <h5> {{character.category}}</h5>
        <h5> {{character.status}}</h5>
    </div>
</template>

<style lang="scss" scoped>
    .character-card{
        width: calc(100% / 6 - 10px);
        background-color:  rgb(26, 26, 33);
    
        h4{
            color: white;
        }

        h5{
            color: gray;
        }
    }



</style>