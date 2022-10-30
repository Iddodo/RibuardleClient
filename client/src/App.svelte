<script>
    import LetterBox from './assets/LetterBox.svelte';
    import RibuardleBoard from './assets/RibuardleBoard.svelte';
    
    let user_input = '';
    let total_turns = 10;
    let current_turn = 1;
    let current_character_in_turn = 0;

    let ribuardle_words = {
        topHorizontal: ['', '', '' ,'', ''],
        midHorizontal: ['', '', '' ,'', ''],
        bottomHorizontal: ['', '', '' ,'', ''],
        leftVertical: ['', '', '' ,'', ''],
        midVertical: ['', '', '' ,'', ''],
        rightVertical: ['', '', '' ,'', ''],
    };
    
    const currentTermMapping = (turn) => {
        switch ((turn - 1) % 3) {
            case 0: return ["topHorizontal", "rightVertical"];
            case 1: return ["midHorizontal", "midVertical"];
            case 2: return ["bottomHorizontal", "leftVertical"];
        }
    };

    const hebrew_map = "שנבגקכעיןחלךצמםפ/רדאוה׳סטז";
    const hebrew_alphabet = "אבגדהוזחטיכלמנסעפצקרשת";
    
    const mapLetterKeyToHebrew = (code) => {
        if (code == 188) return 'ת';

        return hebrew_map[code - 65];
    };

    const onKeyDown = (e) => {
        
        // Backspace detected
        if (e.keyCode == 8) {
            currentTermMapping(current_turn).forEach((word) => {
                ribuardle_words[word][current_character_in_turn] = '';
            });
            current_character_in_turn--;
            ribuardle_words = ribuardle_words;
            return;
        }
        // not a letter
        if (!(e.keyCode >= 65 && e.keyCode <= 90 || e.keyCode == 188)) {
            return;
        }
        
        const ch = mapLetterKeyToHebrew(e.keyCode);
        
        // not a regular hebrew character
        if (!hebrew_alphabet.includes(ch)) {
            return;
        }
        
        // Add character to words of current mapping
        currentTermMapping(current_turn).forEach((word) => {
            ribuardle_words[word][current_character_in_turn] = ch;
        });
        current_character_in_turn++;
        ribuardle_words = ribuardle_words;


       user_input = ch; 

       console.log(ribuardle_words.topHorizontal);
    };
    
    
</script>

<RibuardleBoard {ribuardle_words} />
<svelte:window on:keydown|preventDefault={onKeyDown} />

<style>
    :global(body) {
        background-color: white;
        color: black;
        direction: rtl;
    }

</style>