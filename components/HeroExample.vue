<template>
<div class="hero-example">
    <Stack spacing="lg">
        <slot />

        <Stack spacing="sm">
            <h4>Hey!</h4>
            <h1>Main title</h1>
        </Stack>

        <p>Main description</p>
    </Stack>
</div>
</template>

<style lang="less">
.hero-example {
    color: #fff;
    padding: 4rem;
    text-align: center;
    position: relative;

    background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
        url('https://unsplash.it/1920/1080');
    background-size: cover;
    background-attachment: fixed;
    background-position: center center;
}
</style>