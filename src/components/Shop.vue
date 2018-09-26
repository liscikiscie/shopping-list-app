<template>
    <div class="shop">
        <div class="shopHeader">
            <h1>{{ header }}</h1>
            <div class="add-item-form">
                <input
                        type="text"
                        v-model="newItem"
                        placeholder="Add an item"
                        @keyup.enter="addItemToList"
                >
                <button
                        class="submit-button"
                        @click="addItemToList"
                        v-bind:disabled="newItem.length === 0"
                >Submit
                </button>
            </div>
        </div>
        <ShopItems
                v-for="(item, key) in items"
                :key="item.id"
                :purchased="item.purchased"
                :label="item.label"
                :items="items"
                @removeElement="removeItem(key)"
        />
        <p v-if="items.length === 0"> Your list is empty</p>
    </div>
</template>

<script>
    import ShopItems from './ShopItems';

    let Shop = {
        name: 'Shop',
        components: {
            ShopItems
        },
        data() {
            return {
                header: 'Shopping List App',
                newItem: '',
                items: [
                    {
                        id: 1,
                        label: '20 wine bottle',
                        purchased: false
                    },
                    {
                        id: 2,
                        label: '10 wine glass',
                        purchased: true
                    },
                    {
                        id: 3,
                        label: '1 orange juice',
                        purchased: false
                    }
                ]
            }
        },
        methods: {
            addItemToList: function () {
                this.items.unshift({
                    label: this.newItem,
                    purchased: false,
                    id: this.id()
                });
                this.newItem = '';
            },
            id: function () {
                return Math.floor((Math.random() * 100) + 1);
            },
            removeItem: function ( key ) {
                this.$delete(this.items, key);
            }
        }
    };
    export default Shop;
</script>

<style scoped lang="scss">

    .shop {

        .shopHeader {
            display: flex;
            flex-direction: column;
            height: auto;

            .add-item-form {
                display: flex;
                flex-direction: row;
                align-items: center;
                justify-content: center;

                input {
                    width: 300px;
                    height: 20px;
                    font-size: 20px;
                    padding: 15px;
                    margin: 15px;
                }

                .submit-button {
                    height: 20px;
                    width: auto;
                    padding: 0 15px;
                }
            }
        }
    }

</style>
