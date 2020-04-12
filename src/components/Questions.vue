<template>

    <div class="jumbotron jumbotron-fluid">
        <div class="container-fluid">
            <h2>Would you rather...</h2>

            <p>
                {{question}}
            </p>

            <div v-if="id===0" id="selection">


               <div class="form-check" >
                    <input id="v1" class="form-check-input" type="radio" v-bind:value="answer1" v-model="choices" v-on:change="chosen(choices, id)">
                    <label class="form-check-label" for="v1">{{answer1}}</label>
                </div>
                <div class="form-check" id="selection">
                    <input id="v2" class="form-check-input" type="radio" v-bind:value="answer2" v-model="choices" v-on:change="chosen(choices,id)">
                    <label class="form-check-label" for="v2">{{answer2}}</label>
                </div>


            
            </div>


            <div v-if="id===1" id="selection">
                <div class="form-check">
                    <input id="v1" class="form-check-input" type="radio" v-bind:value="answer1" v-model="choices" v-on:change="chosen(choices, id)">
                    <label class="form-check-label" for="v1">{{answer1}}</label>
                </div>
                <div class="form-check" >
                    <input id="v2" class="form-check-input" type="radio" v-bind:value="answer2" v-model="choices" v-on:change="chosen(choices,id)">
                    <label class="form-check-label" for="v2">{{answer2}}</label>
                </div>

            
            </div>

            <div v-if="id===2" id="selection">
                <div class="form-check">
                    <input id="v1" class="form-check-input" type="radio" v-bind:value="answer1" v-model="choices" v-on:change="chosen(choices, id)">
                    <label class="form-check-label" for="v1">{{answer1}}</label>
                </div>
                <div class="form-check" id="selection">
                    <input id="v2" class="form-check-input" type="radio" v-bind:value="answer2" v-model="choices" v-on:change="chosen(choices,id)">
                    <label class="form-check-label" for="v2">{{answer2}}</label>
                </div>
            </div>
        </div>

    

    </div>
    
</template>


<script>
export default {
    name: "Questions",
    props: {
        question: String,
        answer1: String,
        answer2: String,
        id: Number,
    },
    data() {
        return{
            choices:''
        }
    },
    methods: {
        chosen(choices,id){
            // emit the answer to parents
            this.$emit('answer', choices,id)
        }
    }
    

}
</script>


<style>
*{
    text-align: center;
    margin: 0 auto;
    max-width: 56em;
    padding: 1em 0;
}
h2{
    text-align: left;
    color: grey;
}
p{
    text-align: right;
    font-weight:bolder;
    font-size: 25px;
}

#selection{
    font-size: 20px;
}

</style>