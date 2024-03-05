# Corpus of Taylor Swift (CoTS)

# Introduction

This is a dataset consisting of all song lyric words on all Taylor Swift's studio albums, as well as a selection of other songs written by her. CoTS is generated using 'Taylor's Version' album lyrics where available, and includes all bonus/'from the vault' songs that are not pure remixes.

![CoTS word cloud](img/cots-word-cloud.png)

# Word Categorisation

CoTS categorises lyric word frequencies, word variants and parts of speech (PoS) as defined by the [Word Frequency in Written and Spoken English (WFWSE)](https://ucrel.lancs.ac.uk/bncfreq/flists.html) list. 

Lyric words have also been categorised using the [Oxford 5000 by CEFR level](https://www.oxfordlearnersdictionaries.com/wordlists/oxford3000-5000) word list, which ranks words based on language importance using the Common European Framework of Reference for Languages (CEFR).

CoTS also makes use of the [top 100 most frequent words](https://en.wikipedia.org/wiki/Most_common_words_in_English) of the english language as defined by the Oxford English Corpus (OEC).

To ensure as complete lyric word categorisation as possible the following have been added to WFWSE word variants:

- American word spellings
- common acronyms, eg. `TV` or `FBI` 
- simple contractions, eg. `havin'` or `playin'`
- possesive nouns, eg. `friend's` or `parent's`
- numeric forms of numbers, eg. `13`

# Housekeeping

- Two songs all two well and snow on the beach

## Album Codes

For brevety, CoTS uses the following album codes:

- TSW - Taylor Swift (aka Debut)
- FER - Fearless
- SPN - Speak Now
- RED - Red
- NEN - 1989
- REP - Reputation
- LVR - Lover
- FOL - Folklore
- EVE - Evermore 
- MID - Midnights
- TPD - The Tortured Poets Society
- OTH - Other Songs

# Corpus Parts

The corpus is provided in four parts, representing details and statistics of lyric words, songs, albums and lyrics. Details of the columns that comprise each of these parts are provided below.

## Word Details

This part is the main body of the corpus and lists each lyric word along with various categorisation/statistical/labelling columns related to the word. These are detailed below:

### Word

A word that appears one or more times, in one or more song lyrics. These are primarily presented in lower case, apart from in instances of proper nouns such as `Hollywood` or other ordinarily capitalised nouns such as `January`. Various tenses of the same word are grouped together in the same frequency banding/rank (eg. the words `doing`, `does`, `done`, `did` and `do` all share the same `FqBand`, `OECRank` and `CEFRLevel`).

> [!NOTE]
> Some proper nouns such as place names or names of individuals have been hyphanated to preserve the single word consistency when searching, eg. `New-York`, `Miss-Americana` and `Tim-McGraw`. Additionaly, for clarity the word `I` is listed as `i`.

### PoSes (Part of Speech[es])

These are the standard gramatical categorisations that are assigned to English language words. The English language is comprised of many homographic words, which are words that are spelled the same but have different meanings or origins. Consider the word `close`, which can be an adjective, adverb, noun or verb, or the word `minute` which can be an adjective, noun or verb. As such, multiple PoS categories are often assinged to each lyric word in CoTS, and are listed in order of that word's PoS WFWSE frequency. 

PoS categories appear abbreviated within CoTS as follows:

- Adje - Adjective
- Adve - Adverb
- Arti - Article
- Conj - Conjunction
- Dete - Determiner
- Inte - Interjection
- Infi - Infinitive Marker
- Noun - Noun
- Numb - Number
- Prep - Preposition
- Pron - Pronoun 
- Verb - Verb

Additionaly the following three non-standard categories have been added for contraction words (eg. `doesn't`, `should've`), proper nouns (eg. `London`, `Halloween`, `Emma`) and currently unclassified words:

- Cont - Contraction
- Prop - Proper Noun 
- Uncl - Unclassified

> [!NOTE]
> A small selection of compound words, irregular interjections, non-words etc. (eg. `wine-stained`, `ooh-hoo-hoo`, `3AM`) are currently marked as `Uncl`. These may be classified in future versions of CoTS.

### FqBand (Frequency Band)

This is a word frequency band that each lyric word has been assinged. It has been derived from the WFWSE word frequency and using the [Fibonacci numbers F11 to F24](https://www.math.net/list-of-fibonacci-numbers) as banding intervals, 1 to 16. 

As described in the [PoSes](https://github.com/sagesolar/Corpus-of-Taylor-Swift#poses-part-of-speeches) column, due to the homographic nature of many English language words, many lyric words are assinged multiple word frequency values. In order to present a single frequency band for each lyric word, the highest frequency value PoS of each lyric word was used when calculating a word's frequency band.

> [!NOTE]
> Around 250 lyric words have not been assinged a frequency band, as they are not present in the WFWSE list. These include contractions, proper nouns, compound words and irregular interjections.

### OECRank (Oxford English Corpus Rank)

The top 100 OEC ranked words of the English language are labelled 1-100 in this column. CoTS utilises these ranked words in several parts such as [NextWord](https://github.com/sagesolar/Corpus-of-Taylor-Swift#nextword1-2-3) and [Repeats](https://github.com/sagesolar/Corpus-of-Taylor-Swift#reps-repeats), and is therefore provided here for completeness. Due to WFWSE word variants, some OEC rankings appear more than once in the column, see the [Word](https://github.com/sagesolar/Corpus-of-Taylor-Swift#word) column regarding word groupings.

> [!NOTE]
> Unlike the WFWSE, the OEC categorises the words `a` and `an` seperately, so for the purposes of the OEC rank they are treated as seperate words, with ranks of `6` and `32` respectively. This is the only instance that this denormalisation occurs.

### CEFRLevel (Common European Framework of Reference for Languages Level)

The 5000 most important words of the English language, as defined by the Oxford 5000 CEFR list, are provided, categorised into the following bands in order of word simplicity when learning a language:

- A1
- A2
- B1
- B2
- C1
 
From research, it is not fully clear how to categorise words not included in this list. However they can be interpreted as less important than those words within the list, or more difficult to learn or both.

### NextWord[1-2-3]

Each lyric word in CoTS is listed with its next three most frequently occurring word. For example, the lyric word `high` has the `NextWord[1-2-3]` values:

[ `infidelity (6)`, `heels (4)`, `above (3)` ]

This can be read as the most frequent next word occurrence for the lyric word `high` across all songs/albums is `infidelity`, occurring 6 times. The next most frequent word occurrence is `heels`, occurring 4 times and the one after that is `above`, occurring 3 times. 

If the top two (or more) occurring 'next' words share the same occurrence count, then they are presented in order of Album/Track Number occurrence.

In an effort to increase the interest of these 'next' word lists, and to not innudate them with very common words, the top 50 words of the OEC have been filtered out of this part of CoTS. Furthermore 'next' words occurring at the end of lyric lines, within subsequent parenthesis or after punctioation marks (excluding commas) are not counted. Repeated words are also not counted, as these are instead counted in the [Reps](https://github.com/sagesolar/Corpus-of-Taylor-Swift#reps-repeats) column. For example, consider the following lyrics:

1. >_In a storm, in my best dress, fearless_
2. >_And people would say, "They're the lucky ones"_
3. >_'Cause look at your face (Look at your face; Gorgeous)_
4. >_Trouble, trouble, trouble (Oh)_

In the first example, the words `In`, `storm` and `in` have no 'next' word, as their respective following words `a` and `in` and `my` are in the OEC top 50. Conversely the words `a`, `my`, `best` and `dress`  have respective 'next' words of `storm`, `best`, `dress` and `fearless`.

These rules continue in the second example and on, including the word `say` which has a 'next' word of `They're`, regardless of the double quote character.

In the third example both instances of the word `face` have no 'next' words, as their respective following words `Look` and `Gorgeous` are preceeded by parenthesis or punctioation marks. Notice that the commas in the first two examples do not exclude following words.

Lastly, in the fourth example, the first two instances of the word `trouble` have no 'next' word as they are repititions of eachother (see [Reps](https://github.com/sagesolar/Corpus-of-Taylor-Swift#reps-repeats) column). The third instance of the word `trouble` has no 'next' word as the word `Oh` is enclosed in parenthesis.

### Length

This is the number of characters (including any hyphens) that comprise a lyric word.

### Reps (Repeats)

This is the amount of times that a lyric word is repeated in lyric lines across all songs/albums. For example, consider the following lyrics:

1. >_It just felt so good, good_
2. >_Twenty-two (Oh, oh, oh, oh, oh)_
3. >_That's how you get the girl, girl, yeah, yeah_
4. >_I, I-I-I, I, I, I wish, I wish, I_
5. >_In a getaway car (Oh-oh-oh)_
6. >_Ra-di-di-di-di-di-di-di-di-di-da-da_

In the first three examples, the word `good` would be counted twice, the word `oh` is counted five times, the word `girl` would be counted twice and similar for the word `yeah`.

CoTS splits apart words that have multiple uniform repetitions seperated by hyphens, so in the fourth and fifth examples the word `I` is counted seven times, and the word `oh` is counted three times.

The final example is not counted as any repetititions, as `Ra-di` and later `di-da` are non uniform.

### Count

This is the total count of instances of a lyric word across all songs/albums.

### Verse / Bridge / Chorus / Refrain / InOut (Intro/Outro)

This is the total count of instances of a lyric word in various song structure parts across all songs/albums (if any). For brevety, some similar song structure parts have been grouped together as follows:

- Bridge - (also includes breaks, breakdowns, buildups and interludes)
- Chorus - (also includes pre-choruses and post-choruses)
- InOut - (includes intros, outros, and spoken outros)
- Refrain - (no other inclusions)
- Verse - (no other inclusions)

### AlbumCount

This is the total count of albums that a lyric word occurs at least once on.

### SongCount

This is the total count of songs that a lyric word occurs at least once in.

### AlbumOccurrences

These are a collection of one or more labels representing the albums and corresponding album song count that a lyric word occurs on. 

For example, the lyric word `blood` has the `AlbumOccurrences` values:

[ `NEN#19`, `FOL#2`, `EVE#1`, `MID#7` ]

This is interpreted as the word `blood` occurring 19 times on the album '1989', twice on the album 'Folklore', once on the album 'Evermore' and seven times on the album 'Midnights'.

### SongOccurrences

These are a collection of one or more labels representing the album songs and corresponding times that a lyric word occurs in each song. If a lyric word occurrs on more than five songs, then the first five songs are listed, followed by a `...MANY` label to represent the rest.

For example, the lyric word `kid` has the `SongOccurrences` values:

[ `RED:16#3`, `RED:30#1`, `FOL:10#2`, `EVE:5#2`, `MID:5#4`, `...MANY` ]

This is interpreted as the word `kid` occurring 3 times on track 16 of the album 'Red', once on track 30 of the album 'Red', twice on track 10 of the album 'Folklore', and so on.

## Song Details

This part of CoTS provides summary details and statistics for each song that is included in the dataset.

### Album / Track / Title

A song's album code, track number and title.

### FeaturedArtists

A list of other artists that are featured on a song (if any).

### FromTheVault

Set to `Yes` if the song was released 'from the vault', `No` otherwise.

### LowestFreqWord

The lowest WFWSE frequency word that occurrs in a song. This is effectively the most obscure word in a song according to the WFWSE.

### PrevalentVerb / Adjective / Noun

The most common verb, adjective and noun that occur in a song. This can be seen as giving the song a (likely) unique three word cods. For example the song 'Out Of The Woods' on the album '1989' has the following prevelent verb / adjective / noun combination:

[ `remember`, `clear`, `woods` ]

> [!NOTE]
> In an effort to increase the interest of these prevalent word lists, and to not innudate them with very common words, the top 100 words of the OEC have been filtered out of this part of CoTS. As ever, the homographic nature of English means that some of the chosen words might not be used as their assigned PoS in this part of CoTS, so these three words are provided more for fun. 

### Lines

This is the total count of lyric lines in a song.

### Verses / Bridges / Choruses / Refrains / InOuts (Intros/Outros)

This is the total count of various song structure parts in a song (if any). For brevety, some similar song structure parts have been grouped together as detailed in the [related Word Details section](https://github.com/sagesolar/Corpus-of-Taylor-Swift#verse--bridge--chorus--refrain--inout-introoutro).

### Words

This is the total count of words in a song.

### GeniusUrl

The genius.com link corresponding to a song.

## Album Details

This part of CoTS provides summary details and statistics for each album that is included in the dataset.

###  Code / Title / SubTitle / Year

An album's code, title, subtitle (if any) and release year. 

> [!NOTE]
> For 'Taylor's Version' albums, the year is set to the 'TV' release year.

### LowestFreqWord

The lowest WFWSE frequency word that occurrs on an album. This is effectively the most obscure word on an album according to the WFWSE.

### PrevalentVerb / Adjective / Noun

The most common verb, adjective and noun that occur on an album (see the [related Song Details section](https://github.com/sagesolar/Corpus-of-Taylor-Swift#song-details).

### Songs

This is the total count of songs that are on an album.

### Words

This is the total count of words on an album.

## Lyrics

This part of CoTS provides a flat set of all lyric lines of each song included in the dataset. These are labelled with:

`FOL:03:036` - `I had a marvelous time ruining everything`

## Files
- Corpus
- lyrics
- TSVs
