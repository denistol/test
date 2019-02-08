<template>
    <div class="modal-window" @click.prevent="$emit('hideModalEvent')">
        <h2 v-bind:class="{'text-danger' : msg != 'Success!', 'text-success':msg, }">
            {{msg}}
        </h2>
    </div>
</template>

<script>
export default {
    props:['msg'],
    mounted(){
        setTimeout(()=>this.$emit('hideModalEvent'),2000)
    }
}
</script>
