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
                :item="item"
                :items="items"
                @remove-item="removeItem"
        />
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
                this.items.push({
                    label: this.newItem,
                    purchased: false,
                    id: this.id
                });
                this.newItem = '';
            },
            id: function () {
                return Math.floor((Math.random() * 100) + 1);
            },
            removeItem: function ( key ) {
                console.log('chuj');
                this.$delete(this.item, key);

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
