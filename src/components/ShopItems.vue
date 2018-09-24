<template>
    <div v-else class="shop-items">
        <p v-if="shopList.length === 0"> Your list is empty</p>
        <p>{{ shopItem.label }}</p>
        <button class="removeButton" @click="removeItem">Remove</button>
    </div>
</template>

<script>
    let ShopItems = {
        name: 'ShopItems',
        props: {
            item: Object,
            items: Array
        },
        data() {
            return {
                shopItem: this.item,
                shopList: this.items
            }
        },
        methods: {
            removeItem: function () {
                this.$emit(
                    'remove-item', {
                        label: this.item,
                        id: this.id
                    }
                );
            }
        }
    };
    export default ShopItems;
</script>

<style scoped lang="scss">

    .shop-items {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-direction: row;
        list-style: none;
        max-width: 200px;
        font-size: 120%;

        p {
            height: 20px;
            min-width: 200px;
        }

        .removeButton {
            height: 20px;
            padding: 0 15px;
        }

    }
</style>
