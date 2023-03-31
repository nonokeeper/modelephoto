<template>
    <div class="container bg-slate-300 p-8 mx-auto"><a class="text-cyan-800" href="/">Home</a> About me</div>
    <div v-html="aboutPage"></div>
</template>
<script setup lang="ts">
    let aboutPage = ref('');
    /*
    const aboutPage = await fetch("https://r8pfob1o.directus.app/items/Page?filter={%22slug%22:{%22_eq%22:%22about%22}}");
    console.log(aboutPage.json());
    */
    fetch("https://r8pfob1o.directus.app/items/Page?filter={%22slug%22:{%22_eq%22:%22about%22}}")
    .then(res => res.json())
    .then(result => {
        console.log('result from Directus : ',result);
        console.log('data inside result from Directus : ',result.data);
        aboutPage.value = result.data[0].mainContent;
    })

</script>