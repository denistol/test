<template>
    <iframe :src="snazzyLink" width="100%" height="100%" style="border:none;"></iframe>
</template>
<script>

export default{
    props:['id'],
    computed:{
        snazzyLink(){ return `https://snazzymaps.com/embed/${ this.id || 131842 }` }
    },
}
</script>