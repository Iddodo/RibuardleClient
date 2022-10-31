<script>
    import LetterBox from './assets/LetterBox.svelte';
    import RibuardleBoard from './assets/RibuardleBoard.svelte';
    
    let user_input = '';
    let total_turns = 10;
    let current_turn = 1;
    let current_character_in_turn = -1;
    


    let ribuardle_words = {};

    const ribuardle_labels = [
        'topHorizontal',
        'midHorizontal',
        'bottomHorizontal',
        'leftVertical',
        'midVertical',
        'rightVertical',
    ];

    ribuardle_labels.forEach((label) => {
        ribuardle_words[label] = [
                {letter: '', clues: []},
                {letter: '', clues: []},
                {letter: '', clues: []},
                {letter: '', clues: []},
                {letter: '', clues: []},
            ];
    });

    const intersections = {
        topHorizontal: [
            {target: "leftVertical", own_index: 4, target_index: 0},
            {target: "midVertical", own_index: 2, target_index: 0},
            {target: "rightVertical", own_index: 0, target_index: 0},
        ],
        midHorizontal: [
            {target: "rightVertical", own_index: 0, target_index: 2},
            {target: "midVertical", own_index: 2, target_index: 2},
            {target: "leftVertical", own_index: 4, target_index: 2},
        ],
        bottomHorizontal: [
            {target: "rightVertical", own_index: 0, target_index: 4},
            {target: "midVertical", own_index: 2, target_index: 4},
            {target: "leftVertical", own_index: 4, target_index: 4},
        ],
        leftVertical: [
            {target: "topHorizontal", own_index: 0, target_index: 4},
            {target: "midHorizontal", own_index: 2, target_index: 4},
            {target: "bottomHorizontal", own_index: 4, target_index: 4},
        ],
        midVertical: [
            {target: "topHorizontal", own_index: 0, target_index: 2},
            {target: "midHorizontal", own_index: 2, target_index: 2},
            {target: "bottomHorizontal", own_index: 4, target_index: 2},
        ],
        rightVertical: [
            {target: "topHorizontal", own_index: 0, target_index: 0},
            {target: "midHorizontal", own_index: 2, target_index: 0},
            {target: "bottomHorizontal", own_index: 4, target_index: 0},
        ],
    };
    
    const currentTermMapping = (turn) => {
        switch ((turn - 1) % 3) {
            case 0:
                return ["topHorizontal", "rightVertical"];
            case 1: 
                return ["midHorizontal", "midVertical"];
            case 2:
                return ["bottomHorizontal", "leftVertical"];
        }
    };

    const hebrew_map = "שנבגקכעיןחלךצמםפ/רדאוה׳סטז";
    const hebrew_alphabet = "אבגדהוזחטיכלמנסעפצקרשת";
    
    const mapLetterKeyToHebrew = (code) => {
        if (code == 188 || code == 62) return 'ת';

        return hebrew_map[code - 65];
    };
    

    const onKeyDown = (e) => {
        // Backspace detected
        if (e.keyCode == 8) {
            // Guard current character in turn from below
            if (current_character_in_turn < 0) {
                return;
            }

            currentTermMapping(current_turn).forEach((word) => {
                ribuardle_words[word][current_character_in_turn].letter = '';
            
                intersections[word].forEach((intersected) => {
                    ribuardle_words[intersected.target][intersected.target_index].letter = ribuardle_words[word][intersected.own_index].letter;
                });
            });
            current_character_in_turn--;
            ribuardle_words = ribuardle_words;
            return;
        }

        // Enter
        if (e.keyCode == 13) {
            currentTermMapping(current_turn).forEach((word) => {
                ribuardle_words[word].forEach((letter_obj, index) => {
                   ribuardle_words[word][index].clues.push({ letter: letter_obj.letter, type: 'trololo' });
                });

                ribuardle_words[word] = ribuardle_words[word].map(letter_obj => {
                    return {letter: '', clues: letter_obj.clues};
                });
                
                intersections[word].forEach((intersected, index) => {
                    ribuardle_words[intersected.target][intersected.target_index].letter = '';
                });
            });
            ribuardle_words = ribuardle_words;
            current_turn++;
            current_character_in_turn = -1; 
            return;
        }

        // not a letter
        if (!(e.keyCode >= 65 && e.keyCode <= 90 || e.keyCode == 188 || e.keyCode == 62)) {
            return;
        }
        
        const ch = mapLetterKeyToHebrew(e.keyCode);
        
        // not a regular hebrew character
        if (!hebrew_alphabet.includes(ch)) {
            return;
        }
        
        // Guard current character in turn from above
        if (current_character_in_turn >= 4) {
            return;
        }
        // Add character to words of current mapping
        current_character_in_turn++;
        currentTermMapping(current_turn).forEach((word) => {
            ribuardle_words[word][current_character_in_turn].letter = ch;
            
            intersections[word].forEach((intersected) => {
                ribuardle_words[intersected.target][intersected.target_index].letter = ribuardle_words[word][intersected.own_index].letter;
            });
        });
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