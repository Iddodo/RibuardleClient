<script>
import LetterBox from "./LetterBox.svelte";

let size = "100px";

</script>

<div class="ribuardle-board-grid" style="--ribuardle-box-size: {size}">

<LetterBox id="letter-box-1" {size} />
<LetterBox id="letter-box-2" {size} />
<LetterBox id="letter-box-3" {size} />
<LetterBox id="letter-box-4" {size} />
<LetterBox id="letter-box-5" {size} />
<LetterBox id="letter-box-6" {size} />
<div class="letter-box-empty"></div>
<LetterBox id="letter-box-8" {size} />
<div class="letter-box-empty"></div>
<LetterBox id="letter-box-10" {size} />
<LetterBox id="letter-box-11" {size} />
<LetterBox id="letter-box-12" {size} />
<LetterBox id="letter-box-13" {size} />
<LetterBox id="letter-box-14" {size} />
<LetterBox id="letter-box-15" {size} />
<LetterBox id="letter-box-16" {size} />
<div class="letter-box-empty"></div>
<LetterBox id="letter-box-18" {size} />
<div class="letter-box-empty"></div>
<LetterBox id="letter-box-20" {size} />
<LetterBox id="letter-box-21" {size} />
<LetterBox id="letter-box-22" {size} />
<LetterBox id="letter-box-23" {size} />
<LetterBox id="letter-box-24" {size} />
<LetterBox id="letter-box-25" {size} />
</div>

<style>
    .ribuardle-board-grid {
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        grid-template-columns: repeat(5, 1fr);
    }
    
    .letter-box-empty {
        width: var(--ribuardle-box-size);
        width: var(--ribuardle-box-size);
        
        background-color: black;
    }
</style>