<template>

    <div>
        <ul>
  
            <li v-for="choice in choices" :key="choice.answer">
                {{choice.answer}}
            </li>

        </ul>
        
        
        
    </div>
    
</template>


<script>
export default {
    name: "Answer",
    props: {
        choices: Array
    },
    data() {
        return{
            answer: []
            // choices: []
        }
    }

}
</script>

<style>

</style>