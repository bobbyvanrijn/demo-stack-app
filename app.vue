<template>
<Stack spacing="md">
    <NavExample />
    <HeroExample />

    <Stack direction="vertical" spacing="md">
        <CardExample />
        <CardExample />
        <CardExample />
    </Stack>
</Stack>
</template>

<style lang="less">
body {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    margin: 0;
    padding: 0;
}

main {
    padding-inline: 1rem;
    width: calc(100% - 2rem);
    max-width: 30rem;
    margin-inline: auto;
}
</style>