<template>
      <div id="tooltip" :style="{ top: `${clientY}px`, left: `${clientX}px` }" 
      v-if="show" @mouseout="show = false"> tooltip 
      </div>
</template>

<script>
export default {
name: 'DogBio',
props: ['name','hobbies','motto','weight','length'],
data() {
    return {
        show: false,
        clientX: 0,
        clientY: 0
    }
},
methods: {
    onHover(e) {
        const { clientX, clientY} = e;
        this.show = true;
        this.clientX = clientX;
        this.clientY = clientY;
    }
}
}
</script>

<style scoped>
#container {
    width: 95vw;
    height: 95vh;
    align-items: center;
    display: flex;
    justify-content: center;
}
#tooltip {
    border: 1px solid blue;
    padding: 5px;
    position: absolute;
    background-color: white
}
</style>