### Songmark text format

Songmark is a dsl for song. It's a text format to display lyrics and chords. It can easily be displayed in any text editor.

Songmark files have the **.song** extension.

#### Features:
 - simple edit lyrics and chords (using chord symbols)
 - identify simple rythmic measure (using |)
 - provide the tone of the song
 - differentiate verse from chorus and bridge by optinally labeling sections 
 - metadata support for indexing: title, artist, album, year
 - add extra information: links to audio, video or any page
 - tolerant: programs that interpret it may not failed at parsing it, in the worst case all is interpreted as lyrics. Metadata are optional

#### Encoding
For multi language support it necessary to encode your text in **UTF-8**. 
Be careful to configure your text editor to encode character in **UTF-8** if you using other character than ascii subset character.

#### Syntax

```
=== L'autre finistère (Les innocents)

album = Fous à lier
year = 1992
tone = G
video = http://www.youtube.com/watch?v=LkbzNlfYuiI

Verse:
 G 
Comprendrais tu ma belle qu'un jour fatigué
            F 
J'aille me briser la voix une dernière fois
        Em 
À cent vingt décibels contre un grand châtaignier
 Cm           G 
D'amour pour toi.

Chorus:
 F           Dm7            Em 
 Il est un estuaire un long fleuve de soupirs
          B7                        G 
 Ou l'eau mêle nos mystères et nos belles différences
       F              Dm7         Em 
 J'y apprendrai a me taire et tes larmes retenir
          B7                          G 
 Dans cet autre Finistère aux longues plages de silence.
```

##### Chords line recognizer

regexp chord:
```
^(C|D|E|F|G|A|B)(b|#)?(m|M|min|maj)?((sus)?(b|#)?(2|4|5|6|7|9|10|11|13)?)*(\+|aug|alt)?(\/(C|D|E|F|G|A|B))?$
```
supported chords:

```
C
C7
C9
C11
C13
Cmaj7 
CM7
Cm7	
Cmin7
Cmin7b5	
Cm7/G		
C7sus4			
C7+ 	
C7aug
C7b5		
C7#11		
C7b9		
C7#9		
C7b10
C7b9b13	
C7alt		
C7b10b13
C13#11
```

This javascript code test if every sample chords match the regexp
```javascript
var chordreg = /^(C|D|E|F|G|A|B)(b|#)?(m|M|min|maj)?((sus)?(b|#)?(2|4|5|6|7|9|10|11|13)?)*(\+|aug|alt)?(\/(C|D|E|F|G|A|B))?$/;
var chords = "C C7 C9 C11 C13 Cmaj7 CM7 Cm7 Cmin7 Cmin7b5 Cm7/G C7sus4 C7+ C7aug C7b5 C7#11 C7b9 C7#9 C7b10 C7b9b13 C7alt C7b10b13 C13#11".split(" ");

// test if every chords match the regexp
var result = chords.every(function(chord) {
    return chordreg.test(chord);
});
```

#### Usage
You may just want to edit a new song with **.song** extension like **satisfaction.song** in a simple text editor like: notepad, sublime text or notepad++ or any text editor. NB: Configure the editor in UTF-8 encoding

You will find samples songs in this repos.

A **syntax highlighter** for github and sublime text

Parser and generator are implemented in Java, Javascript and golang and can be used to make your own use of this format

#### References
Existing syntax:
 - http://www.boiteachansons.net/Txt/Les-Innocents/L-autre-Finistere.txt
 - http://en.wikipedia.org/wiki/Chord_%28software%29
 
