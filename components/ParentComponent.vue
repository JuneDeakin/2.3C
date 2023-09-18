<template>
    <div>
        <AppHome :title="pageTitle" ></AppHome>
    </div>
</template>

<script>
import AppHome from './AppHome.vue';

export default {
    components: {
       AppHome: AppHome,
    },
    data() {
        return {
            pageTitle: 'The Endangered Birds of NZ',
        };
    },
};
</script>
