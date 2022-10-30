<script>
import LetterBox from "./LetterBox.svelte";

$: {
    window.alert("Change")
}

export let ribuardle_words;

let size = "100px";

</script>

<div class="ribuardle-board-grid" style="--ribuardle-box-size: {size}">

<LetterBox id="letter-box-1" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-2" {size} character={ribuardle_words.topHorizontal[1]} />
<LetterBox id="letter-box-3" {size} character={ribuardle_words.topHorizontal[2]} />
<LetterBox id="letter-box-4" {size} character={ribuardle_words.topHorizontal[3]} />
<LetterBox id="letter-box-5" {size} character={ribuardle_words.topHorizontal[4]} />
<LetterBox id="letter-box-6" {size} character={ribuardle_words.topHorizontal[0]} />
<div class="letter-box-empty"></div>
<LetterBox id="letter-box-8" {size} />
<div class="letter-box-empty"></div>
<LetterBox id="letter-box-10" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-11" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-12" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-13" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-14" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-15" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-16" {size} character={ribuardle_words.topHorizontal[0]} />
<div class="letter-box-empty"></div>
<LetterBox id="letter-box-18" {size} character={ribuardle_words.topHorizontal[0]} />
<div class="letter-box-empty"></div>
<LetterBox id="letter-box-20" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-21" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-22" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-23" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-24" {size} character={ribuardle_words.topHorizontal[0]} />
<LetterBox id="letter-box-25" {size} character={ribuardle_words.topHorizontal[0]} />
</div>

<style>
    .ribuardle-board-grid {
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        grid-template-columns: repeat(5, 1fr);
    }
    .letter-box-empty {
        width: var(--ribuardle-box-size) * 1.1;
        width: var(--ribuardle-box-size) * 1.1;
        
        background-color: black;
    }
</style>