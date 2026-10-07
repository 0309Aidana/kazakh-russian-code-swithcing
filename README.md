# Kazakh-Russian Code-Switching Detector
A small Python project that detects language mixing in Kazakh-Russian sentences.

## Question

How often do Kazakh speakers switch between Kazakh and Russian inside one sentence, and inside one word?

## Method

Each word gets a label:

- KAZ: contains Kazakh-specific letters (ә, і, ң, ғ, ү, ұ, қ, ө) or is in a hand-built Kazakh word list
- RUS: contains Russian-specific letters (э, ь, ъ, ф, ч, щ, ц) or is in a hand-built Russian word list
- MIX: a Russian root with a Kazakh ending ( e.g "теманы"), or a word with both letter sets
- ?: unknown word

A switch is counted where the label changes between two neighboring known words. Unknown words are skipped.

## Data

- 82 training sentences, used to build the word lists
- 20 test sentences, never added to the word lists
- Written by me and my classmates, anonymous, with permission
  
## Results

Training set (82 sentences, 412 words):

- KAZ 270, RUS 118, MIX 22 words, Unknown 2
- Avarage switches per centence: 2.2

Test set (116 words, never added to the word lists):

- KAZ 65, RUS 19, MIX 1, Unknown 31
- 27% of words were unknown
- About 95% of labeled words were correct (81 out of 85)

## Errors found

- Russian root + Kazakh ending were labeled wrongly (e.g "чатты", "детальге", "прогулкаға")
- Words shared by both languages cannot be labeled by letters (e.g "не", "кино")
  
## Limitations

- Unknown words are skipped, so the number of switches is probably underestimated. In one fully Russian clause, every word was unknown.
- Small dataset from one social circle, not representative of all Kazakh speakers.
- The tool cannot split a word into root and ending, so MIX words need manual lists
- Unknown words rose from 0,5% (training) to 27% (test), so the word lists do not generalize well to new sentences.
