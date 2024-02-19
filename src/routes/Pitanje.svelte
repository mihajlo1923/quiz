<script>
    export let question;
    export let correctAnswer;
    export let incorrectAnswers;

    
    let shuffle =(array)=>array.sort(()=> Math.random()-0.5);
    let posssibleAnswers =shuffle([...incorrectAnswers, correctAnswer]);
    const handleClick=(da)=>{
        if(da==correctAnswer){
            alert("Tacno")
        }
        else{
            alert("netacan odgovor")
        }

    }
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