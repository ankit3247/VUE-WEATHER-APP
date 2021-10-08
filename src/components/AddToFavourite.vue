<template>
    <h1 v-my-on:click="addcity">Add City</h1>
</template>

<script>
    export default {
        methods: {
            addcity() {
                alert('CityAdded!');
            }
        },
        directives: {
            'my-on': {
                bind(el, binding, vnode) {
                    console.log('bind');

                    el.addEventListener('click',()=>{
                        console.log('bind');
                        vnode.context.$emit('click');
                    });
                },

            }
        }
    }
</script>