# Human Language Technologies Reports
## Assignment 1
I compared the styles of language used in two different music genres, pop and hip hop, in the 1980s, using natural language processing (NLP) as an aid. I preprocessed song lyrics in text format to support later NLP tasks. I used the Natural Language Toolkit (NLTK) to perform some NLP tasks, including tokenizing song lyrics, removing stop words from the resulting tokens, and stemming tokens. I also wrote code to count the number of rhymes in songs, using the following heuristic to detect rhymes. I assume rhymes occur in adjacent lines in song lyrics and a rhyme occurs when the last words of a pair of adjacent lines are different, alphanumeric, at least 2 letters long, and have a matching couple of last characters.

#### My findings
1. Hip hop songs have a far higher average number of words than pop songs.
2. Hip hop songs have a far higher average number of rhymes than pop songs (and perhaps songs of other genres too).
3. Pop and hip hop songs have similar average lexical diversities (lexical diversity is the number of unique words divided by the number of words).
4. The top 10 most frequent words in both pop and hip hop songs convey little more information about the topics of songs than the songs' titles.
5. The top 10 most frequent non-stop words of a pop song usually conveys far more information about the topic and emotions of the pop song.
6. The top 10 most frequent stems of non-stop words of pop or hip hop songs convey little more information about the songs than their top 10 most frequent non-stop words.

I also describe some flaws in my approach to detecting rhymes and discuss how these flaws could be remedied by some NLP techniques, including using phonemic transcriptions of the lyrics of songs, detecting phonemes in the audio recordings of songs, recognizing similar patterns of phonemes, and detecting rhymes that occur on the same line or two lines apart.

## Assignment 2
I used the language modelling tool [LMTool](http://www.speech.cs.cmu.edu/tools/lmtool-new-debug.html) to generate phonemic transcriptions of 10 words beginning with the letter c. I then slightly modified these phoneme representations and placed syllable boundaries (denoted by $) in them.

| Words | LMTool Phoneme Representations | Modified Phoneme Representations |
| :--- | :---: | :---: |
| Cabins | K AE B AH N Z | K AE B $ IH N Z |
| Cable  | K EY B AH L | K EY $ B AH L |
| Camaraderie | K AA M ER AA D ER IY | K AE $ M AE $ R AE $ D ER $ IY |
| Campgrounds | K AE M P G R AW N D Z | K AE M P $ G R AW N D Z |
| Capable | K EY P AH B AH L | K EY $ P AX $ B AH L |
| Civilization | S IH V AH L IH Z EY SH AH N | S IH $ V AH L $ AY Z $ EY $ SH AH N |
| Conservationists | K AA N S ER V EY SH AH N IH S T S | K AA N $ S ER $ V EY $ SH AH N $ IH S T S |
| Coyotes | K AY OW T IY S | K AY $ OW $ T IY S |
| Cry | K R AY | K R AY |
| Crystals | K R IH S T AH L Z | K R IH $ S T AH L Z |

Then I designed a phonotactic transducer to model the syllables in these words. This phonotactic transducer is depicted in the image below. The onsets, peaks and codas of these syllables respectively begin and end in the states 0 and 1, 1 and 2, and 2 and 3. The phonotactic transducer also models well-formed syllable codas that aren't in the above words. These are M, L P, M Z, N P, M D Z, L D Z, S P S (as in crisps), L P S, L T S, M P S, M T S, N P S and N T S. Some of these may not actually occur in English, but they still sound natural in English—they're well-formed.

![phonotactictransducer](https://user-images.githubusercontent.com/10984620/224857409-949cfad3-c695-40f9-b1f4-7408d2890867.PNG)

I also used LMTool to produce an n-gram model for just the syllables in the words above. I analyzed this model to discover the most common phonemes of the following types in these syllables: vowels, consonants, first phonemes, consonants following the most common vowel, vowels following the most common consonant.
