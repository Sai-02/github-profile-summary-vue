<template>
    <div>
        FollowersList
    </div>
</template>

<script>
import { toRef } from 'vue';

export default {
    name: "FollowersList",
    props: ["followersData"],
    setup(props) {
        const updatedProps = toRef(props)
        console.log("followers data is ", updatedProps)
    },
    watch: {
        updatedProps: (val) => console.log(val)
    }
}
</script>

<style scoped></style>