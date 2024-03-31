<template>
    <svg width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" class="loader-icon">
        <circle class="spinner_S1WN" cx="4" cy="12" r="3" />
        <circle class="spinner_S1WN spinner_Km9P" cx="12" cy="12" r="3" />
        <circle class="spinner_S1WN spinner_JApP" cx="20" cy="12" r="3" />
    </svg>
</template>

<script>
export default {
    name: "LoaderComponent"
}
</script>

<style scoped>
.spinner_S1WN {
    animation: spinner_MGfb .8s linear infinite;
    animation-delay: -.8s;
    background-color: blue;
}

.spinner_Km9P {
    animation-delay: -.65s;
    background-color: blue;
}

.spinner_JApP {
    animation-delay: -.5s;
    background-color: blue;
}

@keyframes spinner_MGfb {

    93.75%,
    100% {
        opacity: .2
    }
}

.loader-icon {
    color: blue;
    font-size: 3rem;
}
</style>