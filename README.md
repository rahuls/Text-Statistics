# PHP Text Statistics

[![Build Status](https://travis-ci.org/DaveChild/Text-Statistics.svg?branch=master)](https://travis-ci.org/DaveChild/Text-Statistics) [![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/DaveChild/Text-Statistics/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/DaveChild/Text-Statistics/?branch=master) [![Code Coverage](https://scrutinizer-ci.com/g/DaveChild/Text-Statistics/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/DaveChild/Text-Statistics/?branch=master)

The PHP Text Statistics class will help you to indentify issues with your website content, especially with readability.

It allows you to measure the readability of text using common scoring systems, including:
* Flesch Kincaid Reading Ease (The higher the score easier to read)
* Flesch Kincaid Grade Level [Notes](https://en.wikipedia.org/wiki/Flesch%E2%80%93Kincaid_readability_tests)
* Gunning Fog Score - estimates the years of formal education a person needs to understand the text [wiki](https://en.wikipedia.org/wiki/Gunning_fog_index)
* Coleman Liau Index - Same as the 2nd index [Notes](https://readable.com/blog/the-coleman-liau-index/)
* SMOG Index - a better and simple alternative to gunning fox index.
* Automated Reability Index - calculates grade similar to smog index.
* Dale-Chall Readability Score - Readability score.
* Spache Readability Score - suitable for only 4th grade students.

One of the biggest challenges with measuring text readability is the counting of syllables, which can be tricky to work out. There are rules in the Statistics class for working out the syllable count of words, and a large list of words to test these rules against.

Please feel free to add to the test word list, especially if you can find words whose syllable count is not correctly calculated (even more especially if you can also add code to the class so your word is correctly handled!).

Homographs are going to be impossible to calculate as they depend on context (i.e., "he moped around the house", "she rode her moped to school), but there are few enough of these not to be a concern. There is a by-no-means-comprehensive list of these in the resources folder.

## Installation

### Using Composer
```json
    {
        "require": {
            "davechild/textstatistics": "1.*"
        }
    }
```    

> If using a version of PHP < 7.2, specify version 1.0.2.

### Measuring Readability

```php
use DaveChild\TextStatistics as TS;
$textStatistics = new TS\TextStatistics;
$text = 'The quick brown fox jumped over the lazy dog.';
echo 'Flesch-Kincaid Reading Ease: ' . $textStatistics->fleschKincaidReadingEase($text);
```

### More Text Shenanigans!

Included with this package are several classes with static methods which can be called independently. If required, you can pass a text encoding to these methods as a second parameter.

#### Pluralise and Singularise Words

```php
echo DaveChild\TextStatistics\Pluralise::getPlural('banana'); // bananas
echo DaveChild\TextStatistics\Pluralise::getSingular('bananas'); // banana
```

#### Count Syllables

```php
echo DaveChild\TextStatistics\Syllables::syllableCount('banana'); // 3
```

#### Letter, Sentence, Word Counts

```php
echo DaveChild\TextStatistics\Text::textLength('I ate a banana.'); // 15
echo DaveChild\TextStatistics\Text::letterCount('I ate a banana.'); // 11
echo DaveChild\TextStatistics\Text::wordCount('I ate a banana.'); // 4
echo DaveChild\TextStatistics\Text::sentenceCount('I ate a banana.'); // 1
```

## Useful Links

**Homepage and Live Version**

https://readable.io/

**JavaScript Port**

https://github.com/cgiffard/TextStatistics.js

**License**

http://www.opensource.org/licenses/bsd-license.php
