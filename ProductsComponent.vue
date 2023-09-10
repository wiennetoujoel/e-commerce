<template>
    <div class="container">
        <h1 class="product-title">Products</h1>
        <table>
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Description</th>
                    <th>Stock</th>
                    <th>Price</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(product, index) in products" :key="index">
                    <td>{{ product.name }}</td>
                    <td>{{ product.description }}</td>
                    <td>{{ product.stock }}</td>
                    <td>Rp{{ product.price }}</td>
                    <td>
                        <button class="addButton button-68" @click="addToCart(product)">Add To Cart</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default{
        props:{
            products:Array
        },

        methods:{
            addToCart(product){
                this.$emit('add-to-cart',product)
            }
        }
    }


</script>
