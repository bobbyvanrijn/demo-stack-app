<template>
<div class="card-example">
    <Stack
        element="a"
        href="#"
        spacing="xl"
        direction="vertical"
        directionSm="horizontal"
    >
        <img src="https://unsplash.it/500/500" alt="Placeholder image" />

        <Stack spacing="sm">
            <h3>Card title</h3>
            <p>Card description</p>

            <Stack direction="row" spacing="sm">
                <Button>Primary</Button>
                <Button variant="secondary">Secondary</Button>
            </Stack>
        </Stack>
    </Stack>
</div>
</template>

<style lang="less">
.card-example {
    padding: 1rem;
    border: 1px solid #eaeaea;
    border-radius: 0.5rem;
    box-shadow: 0 0 1rem rgba(0, 0, 0, 0.1);

    img {
        flex: 0 0 50px;
        width: 100px;
        border-radius: 0.5rem;
    }

    --stack-spacing-xl: 2.5rem;

    a {
        color: inherit;
        text-decoration: none;
    }
}
</style>

