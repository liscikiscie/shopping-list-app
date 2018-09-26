<template>
    <div class="shop-items">
        <div class="single-item">
            <p @click="togglePurchase" class="item" :class="{strikeout: this.purchase}">{{ this.label }}</p>
            <button class="removeButton" @click="removeItem">Remove</button>
        </div>
    </div>
</template>

<script>
    let ShopItems = {
        name: 'ShopItems',
        props: {
            purchased: Boolean,
            label: String,
            items: Array,
            id: Number
        },
        data() {
            return {
                shopList: this.items,
                purchase: this.purchased
            }
        },
        methods:
            {
                removeItem: function () {
                    this.item = {
                        purchased: this.purchased,
                        label: this.label,
                        id: this.id
                    };
                    this.$emit(
                        'removeElement', this.item);
                },
                togglePurchase: function () {
                    this.purchase = !this.purchase;
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

        .single-item {
            display: flex;
            align-items: center;
            flex-direction: row;
            justify-content: flex-start;

            .item {
                cursor: pointer;
            }

            .strikeout {
                color: orange;
                text-decoration: line-through;
            }
        }
    }
</style>
