<template>
    <button class="btn" :class="$attrs.class" @click.prevent="onclick( $event )">{{ btnName }}</button>
</template>

<script>
export default {
    props: {
        btnName: String,
        itemList: Array,
        isAccessories: String,
        index: Number
    },

    methods: {
        onclick( event ) {
            if ( this.isAccessories == "true" ) {
                this.$emit( "onclickData", { itemName: this.btnName, item: this.itemList, index: this.index } )
            }
            else {
                this.$emit( "activeItem", this.index )
            }
        }
    },
}
</script>

<style  scoped>
.btn {
    padding: 0.5rem 1.5rem;
    margin: 0.2rem;
    border: 2px solid #5596F6;
    border-radius: 20px;
    background-color: white;
    color: #5596F6;
    font-weight: 500;
    font-size: 1rem;
    cursor: pointer;
    transition: All 0.3s;

}

.btn:hover,
.active {
    background-color: #5596F6;
    color: white;
}

.btn:active {
    background-color: #2663be;
}
</style>