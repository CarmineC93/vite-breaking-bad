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
        <div class="pic">
            <img :src="character.img" :alt="character.name">
        </div>
        <div class="text">
            <h5>{{character.name}}</h5>
            <h6> {{character.category}}</h6>
            <h6> {{character.status}}</h6>
        </div>

    </div>
</template>

<style lang="scss" scoped>
    .character-card{
        background-color:  rgb(26, 26, 33);
        
        .pic{
            padding: 1rem;
            img{
                height: 200px ;
                max-height: 200px;
                object-fit: cover;
                object-position: top;
            }
        }

        .text{
            padding-bottom:  1rem;

            h5{
                font-size: .8rem;
                color: white;
                text-transform: uppercase;
            }

            h6{
                color: gray;
            }
        }
    }



</style>