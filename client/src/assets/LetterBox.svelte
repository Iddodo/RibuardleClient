<script>
    export let id;
    export let size;

    export let character = '';
</script>

<div class="letter-box-wrapper" id="letter-box-{id}" style="--total-box-size: {size}">
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    <div class="letter-box-clue">
        C
    </div>
    

    <div class="letter-box-character">
        {character}
    </div>
    
    
    
    
    
</div>

<style>
    :root {
        --letter-box-size: 25%;
    }

    .letter-box-character {
        grid-column: 2 / 4;    
        grid-row: 2 / 4;    
        
        margin: 35%;

        font-size: 2em;
        
        
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;

        width: var(--letter-box-size);
        height: var(--letter-box-size);
        
    }

    .letter-box-wrapper {
        display: grid;

        grid-template-columns: var(--letter-box-size) var(--letter-box-size) var(--letter-box-size) var(--letter-box-size);
        grid-template-rows: var(--letter-box-size) var(--letter-box-size) var(--letter-box-size) var(--letter-box-size);
        

        border: 1px black solid;
        
    }
    
    .letter-box-clue  {
        width: var(--letter-box-size) * 1.2;
        height: var(--letter-box-size) * 1.2;
    }

    .letter-box-wrapper {
        width: var(--total-box-size);
        height: var(--total-box-size);
    }
</style>

<!--

<style>
    border-color: black;
.letter-box {
        background-color: red;
        width: 100px;
        height: 100px;
        text-align: center;
    }
</style>
-->