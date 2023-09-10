<template>
    <div>
        <h1>Selamat Datang di Toko Joel</h1>
        <products-component :products="products" @add-to-cart="addToCart"/>
        <cart-component :cart-items="cartItems"/>
       
    </div>
</template>

<script>
import ProductsComponent from './ProductsComponent.vue';
import CartComponent from './CartComponent.vue';

export default{
    data(){
        return{
            products:[
                {name:'Produk A', description :'Anda Sopan Kami Segan', stock : 10, price:10000},
                {name:'Produk B', description :'Anda Baik Kami Curiga', stock : 20, price:20000},
                {name:'Produk C', description :'Pinjam dulu seratus', stock : 30, price:30000},
            ],
            cartItems:[]
        };
    },
    components:{
        'products-component':ProductsComponent,
        'cart-component' : CartComponent
    },
    methods:{
        addToCart(product){
            const existingItem = this.cartItems.find(item => item.product === product);
            if (existingItem) {
                if(product.stock > 0){
                    existingItem.quantity++;
                    product.stock--;
                }else{
                    alert('Produk tidak cukup / sudah habis!');
                }
             }else{
                if (product.stock > 0){
                    product.stock--;
                    this.cartItems.push({product, quantity: 1});
                }else{
                    alert('Produk tidak cukup. sudah habis!');
                }
             }           
        }
    }
};
</script>