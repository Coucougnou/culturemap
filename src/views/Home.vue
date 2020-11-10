<template>
    <span>
        <home-hero></home-hero>
    
        <home-plans></home-plans>
        <home-footer></home-footer>
    </span>
</template>

<script>
import HomeHero from '@/components/HomeHero';
//import HomeMap from '@/components/HomeMap';

import HomePlans from '@/components/HomePlans';

import HomeFooter from '@/components/HomeFooter';

export default {
    name: 'home',
    components: {
        HomeHero,
        //HomeMap,
        HomePlans,
        HomeFooter,
    }
};
</script>