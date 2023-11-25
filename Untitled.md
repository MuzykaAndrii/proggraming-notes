I have telegram bot to remember my sets of vocabularies, each vocabulary contain sets of language pairs with word and translation. I need to create python regex to validte user input language pair, and further parse it and save to db. I will send to u valid and invalid examples and u should send me python regex to validate it.

valid:
(word pair, devided by "-" and separated by new line)
word - translation

(case dont matter)
AnOTHer - TranslationN

(word and translation can contain several words)
some long word - another long transaltion

(separate sign "-" can be with spaces around or without)
word-translation
word -translation
word- translation

(translation can contain ",")
word - translation, another translatiion
word, some - translation

(pair can contain cyryllic symbols)
some - деякий
інший - another

invalid:
(missing "-" symbol)
word translation
another word another translatoin

(allowed only one language pair (one row))
some word - traanslation
another - translation

(allowed only one "-" symbol)
word - translatioon - another

(pair should contain word and translation both)
word - 
-translation

(separate sign can be only "-")
word: translation
