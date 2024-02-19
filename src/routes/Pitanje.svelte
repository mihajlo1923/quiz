<script>
    import { onMount } from 'svelte';
    export let question;
    export let correctAnswer;
    export let incorrectAnswers;

    
    let shuffle =(array)=>array.sort(()=> Math.random()-0.5);
    $:posssibleAnswers =shuffle([...incorrectAnswers, correctAnswer]);
    const handleClick=(da)=>{
        if(da==correctAnswer){
            alert("Tacno")
        }
        else{
            alert("netacan odgovor")
        }

    }
    let data;
    const getQuestion= async()=>{
        const res=await fetch('https://opentdb.com/api.php?amount=1&category=21&difficulty=easy&type=multiple')
        let data=await res.json()
        console.log(data)
        question=data.results[0].question;
        correctAnswer=data.results[0].correct_answer
        incorrectAnswers=data.results[0].incorrect_answers
    }
    onMount(getQuestion)
</script>
<div>
    <h3>
        {@html question}
    </h3>
    <div id="answers">
        {#each posssibleAnswers as pa,i}
        <button on:click={()=>handleClick(pa)}>{pa}</button>
        {/each}
    </div>
</div>