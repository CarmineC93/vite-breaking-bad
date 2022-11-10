<script>
export default {
    name: "AppHeader"
}
</script>

<template>
    <header class="py-2">
        <h1 class="header-title">
            <img class="logo" src="../assets/img/kisspng-walter-white-television-show-logo-amc-breaking-bad-5abba540e853e7.4609369915222469769516.jpg" alt="">
            Breaking Bad Api
        </h1>
    </header>

    <div class="container">
        <div class="selection"> Select Category &#8681; </div>
    </div>

</template>

<style lang="scss" scoped>
.header-title {
    color: white;
}

.logo{
    width: 50px;
}

.selection{
    padding: 0.5rem 1rem;
    width: 160px;
    background-color: white;
    margin: 2rem;
}

</style>