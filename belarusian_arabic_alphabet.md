# Belarusian arabic alphabet and the conversion prompt

Below is my attempt to create a prompt that could convert texts in the Belarusian language from the Cyrillic/Latin script to the Arabic script. It's not just a joke :) The Belarusian-Arabic script really exists, or, to be more exact, existed in the past. What do we know about it? An article from Wikipedia would be enough for some high-level introduction:

`The Belarusian Arabic alphabet or the Belarusian Arabica was based on the Perso-Arabic script and was developed in the 15th or 16th century. The Belarusian Arabic alphabet was used by the Lipka Tatars, who had been invited to settle in the eastern territories of the Grand Duchy of Lithuania—a region that now comprises modern-day Belarus. During the 14th–16th centuries they gradually stopped using their own language and started using the Ruthenian language (modern Belarusian and Ukrainian) rendered in the Belarusian Arabic alphabet. Books of that literary tradition are known in Belarusian as 'Kitab', which is Arabic for 'book' or 'written material'.` 

You can read the full article [here](https://en.wikipedia.org/wiki/Belarusian_Arabic_alphabet).

## The alphabet itself

In the prompt, the AI is instructed to refer to the table below when trying to convert a text. Before a conversion attempt, we can use a pre-prompt like `See the table below? Let's remember it for our further work.`
### Vowels
| Cyrillic | Latin | Final | Medial | Initial | Sound |
|----------|---------|-------------------------------|-------------------------------|-------------------------------|--------|
| А а      | A a     | اَ                            | اَ                            | اَ                            | Like “a” in English “apple” (short open front unrounded vowel), e.g., أب (ʾab) |
|          |         |                               |                               | آ                            | Like “a” in English “father” (long open front vowel), e.g., آدم (ʾĀdam) |
|          |         |                               |                               | عاَ                          | Same as above with pharyngeal onset, e.g., عام (ʿām) |
|          |         | ◌ٰ                            | ◌ٰ                            |                               | Shortened or contextually long “a”, vowel diacritic, e.g., على (ʿalā) |
|          |         | ـي◌َ                          | ـيـ◌َ                          |                               | Diphthong or long “ā” with “y” coloring, e.g., حياة (ḥayāt) |
|          |         | ـى◌َ                          |                               |                               | Alternate long “ā”, often final form |
|          |         | ـي◌ٰ                          | ـيـ◌ٰ                          |                               | Long “ā” with both yā’ and alif signs, e.g., عليا (ʿulyā) |
|          |         | ـى◌ٰ                          |                               |                               | Same as above, alternate notation |
| О о, У у | O o, U u| ◌ُ                            | ◌ُ                            | اُ                            | Like “u” in English “put” (short close back rounded vowel), e.g., أم (ʾumm) |
|          |         | وُ                            | وُ                            | اوُ                           | Long “ū” like “oo” in “food”, e.g., نور (nūr) |
|          |         |                               |                               | عوُ                          | Same as above with pharyngeal onset, e.g., عود (ʿūd) |
|          |         |                               |                               | عُ                           | Short “u” with pharyngeal onset, e.g., عمر (ʿUmar) |
|          |         | وُا                           |                               |                               | Long “ū” diphthongal, e.g., موت (mawt) |
| О о      | O o     | وَ                            | وَ                            | اوَ                           | Like “o” in English “hot” (short mid back rounded vowel), e.g., ولد (walad) |
|          |         |                               |                               | عوَ                          | Same with pharyngeal onset, e.g., عوض (ʿiwaḍ) |
| Э э      | E e     | ◌َ                            | ◌َ                            |                               | Like “e” in English “pen” (short open-mid front unrounded vowel), e.g., قمر (qamar) |
|          |         |                               |                               | عَ                           | Same with pharyngeal onset, e.g., عبد (ʿabd) |
| І і, Ы ы | I i, Y y| ◌ِ                            | ◌ِ                            | اِ                            | Like “i” in English “bit” (short close front unrounded vowel), e.g., اسم (ism) |
|          |         | ـي◌ِ                          | ـيـ◌ِ                          | اِيـ                          | Long “ī” like “machine”, e.g., دين (dīn) |
|          |         | ـى◌ِ                          |                               |                               | Alternate spelling of long “ī”, often final |
|          |         |                               |                               | عِ                           | “i” with pharyngeal onset, e.g., علم (ʿilm) |
|          |         | ـي◌ٖ                          |                               |                               | Variant of “ī” with Kashmiri-style diacritic, rarely used |
|          |         | ـى◌ٖ                          |                               |                               | Same, alternate representation |
### Consonants

| Cyrillic   | Latin     | Final| Medial | Initial | Isolated | Sound                                                                 |
|------------|-------------|-----------|-----------|-------------|-------------|------------------------------------------------------------------------|
| Б б        | B b         | ـب        | ـبـ        | بـ          | ب           | Like 'b' in English 'bat' (voiced bilabial stop), e.g., باب (bab)      |
| В в        | V v         | ـو        | ـو        | و           | و           | Like 'v' in English 'voice' (voiced labiodental fricative), e.g., وفا (wafa) |
| Г г        | H h         | ـه        | ـهـ        | هـ          | ه           | Like 'h' in English 'hat' (voiceless glottal fricative), e.g., هو (huwa) |
| Ґ ґ        | G g         | ـغ        | ـغـ        | غـ          | غ           | Like French 'r' or Arabic ‘gh’ (voiced uvular fricative), e.g., غدًا (ghadan) |
| Д д        | D d         | ـد        | ـد        | د           | د           | Like 'd' in English 'dog' (voiced alveolar stop), e.g., دار (dar)       |
| Ж ж        | Ž ž         | ـژ        | ـژ        | ژ           | ژ           | Like 's' in English 'measure' (voiced postalveolar fricative), e.g., زجاج (zujaj) |
| З з        | Z z         | ـض        | ـضـ        | ضـ          | ض           | Like 'z' in English 'zebra' (voiced emphatic alveolar stop), e.g., ضرب (daraba) |
| З з        | Z z         | ـظ        | ـظـ        | ظـ          | ظ           | Like 'z' in English 'zoo' but pharyngealized (voiced emphatic dental fricative), e.g., ظرف (ẓarf) |
| Зь зь      | Ź ź         | ـز        | ـز        | ز           | ز           | Like 'z' in English 'zoo' (voiced alveolar fricative), e.g., زيد (zayd) |
| Зь зь      | Ź ź         | ـذ        | ـذ        | ذ           | ذ           | Like 'th' in English 'this' (voiced dental fricative), e.g., ذلك (dhalika) |
| Й й        | J j         | ـي        | ـيـ        | يـ          | ي           | Like 'y' in English 'yes' (palatal approximant), e.g., يوم (yawm)       |
| К к        | K k         | ـق        | ـقـ        | قـ          | ق           | Like 'k' in English 'sky' (voiceless uvular stop), e.g., قلم (qalam)   |
| Кь кь      | Kj kj       | ـك        | ـكـ        | كـ          | ك           | Like 'k' in English 'kite' (voiceless velar stop), e.g., كتاب (kitab)  |
| Л л, Ль ль | Ł ł, L l    | ـل        | ـلـ        | لـ          | ل           | Like 'l' in English 'light' (alveolar lateral approximant), e.g., لبن (laban) |
| М м        | M m         | ـم        | ـمـ        | مـ          | م           | Like 'm' in English 'man' (voiced bilabial nasal), e.g., ماء (ma’)     |
| Н н, Нь нь | N n, Ń ń    | ـن        | ـنـ        | نـ          | ن           | Like 'n' in English 'no' (alveolar nasal), e.g., نهر (nahr)            |
| П п        | P p         | ـپ        | ـپـ        | پـ          | پ           | Like “p” in English pen (voiceless bilabial plosive), e.g., بابور (steamboat) |
| Р р        | R r         | ـر        | ـر        | ر           | ر           | Like “r” in Spanish “perro” (voiced alveolar trill), e.g., رأس (head)         |
| С с        | S s         | ـص        | ـصـ        | صـ          | ص           | Like “s” in English sun but heavier (voiceless emphatic alveolar fricative), e.g., صلاة (prayer) |
| Сь сь      | Ś ś         | ـث        | ـثـ        | ثـ          | ث           | Like “th” in English think (voiceless dental fricative), e.g., ثوب (garment)  |
| Сь сь      | Ś ś         | ـس        | ـسـ        | سـ          | س           | Like “s” in English see (voiceless alveolar fricative), e.g., سلام (peace)    |
| Сь сь      | Ś ś         | ـڛ        | ـڛـ        | ڛـ          | ڛ           | Variant of “s”, archaic/extended letter used for specificity in some scripts   |
| Т т        | T t         | ـط        | ـطـ        | طـ          | ط           | Like “t” but stronger and deeper (voiceless emphatic alveolar plosive), e.g., طعام (food) |
| Ў ў        | Ŭ ŭ         | ـو        | ـو        | و           | و           | Like “w” in English water or “u” in Uzbek (semi-vowel or approximant), e.g., ولد (boy) |
| Ф ф        | F f         | ـف        | ـفـ        | فـ          | ف           | Like “f” in English fan (voiceless labiodental fricative), e.g., فم (mouth)    |
| Х х        | Ch ch       | ـح        | ـحـ        | حـ          | ح           | Like voiceless pharyngeal fricative, no direct English equivalent, e.g., حب (love) |
| Х х        | Ch ch       | ـخ        | ـخـ        | خـ          | خ           | Like “ch” in German “Bach” (voiceless velar fricative), e.g., خبز (bread)     |
| Ц ц        | C c         | ـࢯ        | ـࢯـ        | ࢯـ          | ࢯ           | Variant Persian character used for [ts] sound, comparable to “ts” in “cats”   |
| Ць ць      | Ć ć         | ـت        | ـتـ        | تـ          | ت           | Like “t” in English ten (voiceless alveolar plosive), e.g., تمساح (crocodile) |
| Ч ч        | Č č         | ـچ        | ـچـ        | چـ          | چ           | Like “ch” in English cheese (voiceless postalveolar affricate), e.g., چاي (tea) |
| Ш ш        | Š š         | ـش        | ـشـ        | شـ          | ش           | Like “sh” in English shoe (voiceless postalveolar fricative), e.g., شمس (sun) |
|            |             | ـا        | ـا        | ا           | ا           | Like long “a” as in father (long low front vowel), e.g., آدم (Adam)           |
|            |             | ـع        | ـعـ        | عـ          | ع           | Voiced pharyngeal fricative, no English equivalent, e.g., عين (eye)           |
|            |             | ـء        | ـء        |             |             | Glottal stop like in “uh-oh” (ʔ), e.g., سأل (he asked)                         |
### The "Ła-La" digraph

| Cyrillic     | Latin      | Final  | Medial   | Initial   | Isolated   | Sound                                                                 |
|--------------|--------------|------------|------------|--------------|--------------|------------------------------------------------------------------------|
| Ла ла, Ля ля | Ła ła, La la | ـلا        | ـلا        | لا           | لا           | L followed by long 'a', like 'la' in 'la-la' |


## The prompt
The prompt itself. Maybe far from perfection - could be further improved. Note, the Cyrillic script is normally used to write in Belarusian nowadays, but the Latin-Belarusian script exists as well, and it's a better option in case we need an input text to "arabize" :)

```
See the text below. The firts 12 lines of one of the most know piece of the classic Belarusian poetry.

Moj rodny kut, jak ty mnie miły!

Zabyć ciabie nie maju siły!

Nie raz, utomleny darohaj,

Žyćciom viasny maje ubohaj,

K tabie ja ŭ dumkach zalataju

I tam dušoju spačyvaju.

O, jak by ja chacieŭ spačatku

Darohu žyćcia pa paradku

Prajści jašče raz, azirnucca,

Sabrać z daroh kamieńni tyja,

Što hubiać siły maładyja, –

K viaśnie b majoj chacieŭ viarnucca.

Try to rewrite the same text but using the symbols:
Vowels – take them from the first table from the following columns: 1. "Final" (for the last symbol of a word), "Medial" (for any symbol in the word except for the first and the last), "Initial" (for the first symbol of a word)
Consonants – 1. "Final" (for the last symbol of a word), "Medial" (for any symbol in the word except for the first and the last), "Initial" (for the first symbol of a word), "Isolated" (for a sole symbol in the word)
Sounds (symbols) combination "Ła ła" or "La la"
Take it from the third table from the following columns: 1. "Final" (for the last symbol of a word), "Medial" (for any symbol in the word except for the first and the last), "Beginning of the word" (for the first symbol of a word), "Isolated" (for a sole symbol in the word)
Note: the initial input text has the symbols corresponding to the symbols from the "Latin" column of three tables.`

If you see no counterparts for a given symbol in a table, just ignore the symbol – don't print it.
```
### The result of one of the conversion attempts
And that is it. 
But please don't expect too much from it :) The Belarusian-Arabic script was introduced many centuries ago when the Belarusian phonology was somewhat different, and the script was designed to reflect how people pronounced the sounds back then, in approximately 16th century, maybe a bit later. And I'm trying to use this alphabet to write in the modern language. Anyway, an interesting experiment, I believe :)
```
ـمـ◌ُـي ر◌ُـدــنــي كـ◌ُـط يـاَـك طــي مــنـ◌ِ◌َ مـ◌ِـلاـي
زاَـبــيــت ◌ِاَـبـ◌ِ◌َ نـ◌ِ◌َ مـاَـيـ◌ُ سـ◌ِـلاـي  
نـ◌ِ◌َ راَـز اُـطـ◌ُـمــلـ◌َـنــي داَـر◌ُـهـاَـي
ژـيــتـ◌ِ◌ُـم و◌ِاَـســنــي مـاَـيـ◌َ اُـبـ◌ُـهـاَـي
ك طـاَـبـ◌ِ◌َ يـاَ و د◌ُـمــكـاَـه زاَـلـاَـطـاَـيـ◌ُ
طاَـم د◌ُ◌ُـيـ◌ُ ســپـاَـچــيــواَـيـ◌ُ
يـاَـك بــي يـاَ ـهـاَ◌ِ◌َـو ســپـاَـچـاَـطــكـ◌ُ
داَـر◌ُـهـ◌ُ ژـيــتـ◌ِاَ پـاَ پـاَـراَـدــكـ◌ُ
پــراَـيــسـ◌ِ يـاَـچـ◌َ راَـز اَـز◌ِـرـنـ◌ُاَ
سـاَـبــراَـت ز داَـر◌ُـه كـاَـمـ◌ِ◌َـنــنـ◌ِ طــيــيـاَ
شـطـ◌ُ هـ◌ُـبـ◌ِاَـت سـ◌ِلاـي مـاَلااَـدــيــيـاَ
ك و◌ِاَـســنـ◌ِ◌َ ب مـاَـيـ◌ُـي هـاَ◌ِ◌َـو و◌ِاَـرـنـ◌ُ
```
