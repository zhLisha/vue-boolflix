<template>
  <div class="header">
    <div class="container flex">
        <div class="logo">
            <span>BOOLFLIX</span>
        </div>

        <!-- Search Section -->
        <div class="user-search">
                
            <label for="movies">
                <input @keyup.enter="getApi()" v-model="userInput"  type="text" placeholder="Cerca">
            </label>
            <button @click="getApi()" class="btn">
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

           console.log('header', this.userInput);
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

       .search-bar {

            input {
               padding: 2px 0 2px 5px; 
               border: transparent;
            //    background-color: $headerColor;
               border-bottom: 1px solid white;
            }
            .btn {
                border: 1px solid white;
                border-radius: 5px;
                padding: 2px 5px;
                margin-left: 10px;
                background-color: $headerColor;
                color: white;
                cursor: pointer;
            }
        } 
    }
}
</style>