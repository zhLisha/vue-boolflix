<template>
  <div class="header">
    <div class="container flex">
        <div class="logo">
            <span>BOOLFLIX</span>
        </div>

        <!-- Search Section -->
        <div class="user-search flex">
            <label for="movies">
                <input @keyup.enter="getApi()" v-model="userInput"  type="text" placeholder="Cerca">
            </label>
            <button @click="getApi()" class="btn flex">
                Cerca
            </button>
        </div>
    </div>
  </div>
</template>

<script>

export default {
    name: 'HeaderComp',
    data() {
        return {
            userInput: ""
        }
    },

     methods: {
        getApi() {
           this.$emit('apiShow', this.userInput);
           this.userInput = '';
        }
    }
}
</script>


<style lang="scss" scoped>
@import '../style/variables.scss';
.header {
    background-color: $headerColor;
    height: 60px;

    .container {
        height: 100%;
        align-items: center;
        justify-content: space-between;

        span {
            color: $mainColorRed;
            font-size: 35px;
            font-weight: 500;
        }
            
        .btn {
            padding: 6px 5px;
        }

        input {
            padding: 6px ;
            border: none;
            outline: none;
        }
    }
}
</style>