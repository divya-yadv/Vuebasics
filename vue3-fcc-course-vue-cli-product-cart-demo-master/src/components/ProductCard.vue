<template>
    <div class="card">
        <div class="card-title">
            {{ item.name }}
        </div>
        <div class="card-body">
            <i class="icofont-10x"></i>
            <form>
                <div class="row">
                    <div class="cell">
                        <label>Type:</label>
                    </div>
                    <div class="cell">
                        <em>{{ item.type }}</em>
                    </div>
                </div>
                <div class="row">
                    <div class="cell">
                        <label>Price:</label>
                    </div>
                    <div class="cell">
                        ${{ item.price["USD"] }}
                    </div>
                </div>
                <div class="row">
                    <div class="cell">
                        <label>Quantity:</label>
                    </div>
                    <div class="cell">
                        <!-- add quantity value from vue , number to get the number not string-->
                        <input type="number" v-model.number=quantity>
                    </div>
                </div>
            </form>
        </div>
        <div class="card-footer">
            <!-- add addToCart functionality -->
            <button @click="addToCart(item.name, quantity)" class="btn btn-light">Add to cart</button>
        </div>
    </div>
</template>

<script>

export default {
    props: [
        'item', 'addToCart'
    ],
    data() {
        return {
            quantity: 0
        }
    }
}
</script>