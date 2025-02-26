# Wuzzler Puzzle Data

This repository contains cryptogram puzzle data for the Wuzzler game, supporting multiple languages. The puzzles are designed with a progressive difficulty system.

## Project Structure

```
wuzzler-puzzle-data/
├── puzzles/
│   ├── languages.json      # Definition of supported languages
│   ├── en/                 # English puzzles
│   │   └── puzzles.json    # 1100+ English cryptogram puzzles
│   └── el/                 # Greek puzzles
│       └── puzzles.json    # 1100+ Greek cryptogram puzzles
├── generate_puzzles.py     # Script to generate basic puzzle content
├── generate_varied_puzzles.py # Script to generate more varied puzzles
├── generate_storyline_puzzles.py # Script to generate narrative-based puzzles
├── analyze_difficulty.py   # Script to analyze and sort puzzles by difficulty
└── README.md               # This file
```

## Puzzle Data Structure

### Languages.json

This file defines the supported languages, their alphabets, and common letters:

```json
{
  "en": {
    "id": "en",
    "name": "English",
    "alphabet": ["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"],
    "commonLetters": ["E","T","A","O","I","N"]
  },
  "el": {
    "id": "el",
    "name": "Greek",
    "alphabet": ["Α","Β","Γ","Δ","Ε","Ζ","Η","Θ","Ι","Κ","Λ","Μ","Ν","Ξ","Ο","Π","Ρ","Σ","Τ","Υ","Φ","Χ","Ψ","Ω"],
    "commonLetters": ["Α","Ε","Ι","Ο","Τ","Σ"]
  }
}
```

### Puzzles.json

Each language has its own puzzles file containing cryptogram puzzles with this structure:

```json
[
  {
    "id": "en-1",
    "level": 1, 
    "text": "PUZZLE TEXT",
    "language": "en",
    "metrics": {
      "textLength": 20,
      "wordCount": 4,
      "uniqueLetters": 12,
      "alphabetCoveragePercent": 46.15,
      "commonLetterPercent": 35.0,
      "letterDistributionEntropy": 92.65,
      "difficultyScore": 58.27
    }
  },
  ...
]
```

When using the storyline-based generator, puzzles have additional fields:

```json
[
  {
    "id": "en-1",
    "level": 1, 
    "text": "PUZZLE TEXT",
    "language": "en",
    "chapter": 1,
    "chapterTitle": "THE FORGOTTEN SCROLLS",
    "metrics": {
      "textLength": 20,
      "wordCount": 4,
      "uniqueLetters": 12,
      "alphabetCoveragePercent": 46.15,
      "commonLetterPercent": 35.0,
      "letterDistributionEntropy": 92.65,
      "difficultyScore": 58.27
    }
  },
  ...
]
```

#### Puzzle Properties

- **id**: Unique identifier for the puzzle (language code + level)
- **level**: Difficulty level (1-1100+)
- **text**: The puzzle text (to be encrypted as a cryptogram)
- **language**: Language code (en, el)
- **chapter**: (Storyline only) Chapter number in the narrative
- **chapterTitle**: (Storyline only) Title of the chapter
- **metrics**: Calculated difficulty metrics:
  - **textLength**: Number of letters in the puzzle
  - **wordCount**: Number of words
  - **uniqueLetters**: Number of unique letters used
  - **alphabetCoveragePercent**: Percentage of the alphabet used
  - **commonLetterPercent**: Percentage of common letters
  - **letterDistributionEntropy**: Measure of letter distribution evenness
  - **difficultyScore**: Calculated difficulty score (0-100)

## Difficulty Progression

The puzzles progress in difficulty across these general levels:

1. **Beginner (Levels 1-100)**: Very short phrases, common vocabulary, high letter repetition
2. **Easy (Levels 101-300)**: Short phrases, common vocabulary, medium letter variety
3. **Medium (Levels 301-500)**: Medium phrases, mixed vocabulary, more letter variety
4. **Hard (Levels 501-750)**: Longer sentences, more complex vocabulary
5. **Expert (Levels 751-1000)**: Complex sentences, advanced vocabulary, rare letters
6. **Challenge (Levels 1000+)**: Challenging phrases, idioms, quotes, minimal repetition

The difficulty calculation considers:
- Length of the text
- Percentage of unique letters used
- Frequency of common vs. rare letters
- Letter distribution evenness

## Game Lore and Storyline

The narrative-based puzzles follow a cohesive storyline about discovering and deciphering ancient knowledge. The story progresses through 10 chapters:

1. **The Forgotten Scrolls**: Discovery of ancient texts with secret codes
2. **Unlocking the Past**: Uncovering the story of an ancient civilization
3. **The Trials Begin**: A series of tests for your decoding abilities
4. **Hidden Truths**: Deeper secrets about the ancient civilization
5. **The Path of Enlightenment**: A journey to find lost cities
6. **Ancient Teachings**: Philosophical wisdom of the ancients
7. **Guardians and Protectors**: Facing those who protect the knowledge
8. **Forgotten Technology**: Discovering advanced ancient technology
9. **The Cosmic Connection**: The deeper purpose of the ancient knowledge
10. **Keepers of the Flame**: Becoming a guardian of wisdom

Each chapter's puzzles relate to its theme, with difficulty progressing throughout the narrative. This provides players with both a challenge and a rewarding storyline that unfolds as they solve more puzzles.

## Usage

### Generating Basic Puzzles

To generate the basic set of puzzles:

```bash
python generate_puzzles.py
```

### Generating More Varied Puzzles

To generate a more varied set of puzzles:

```bash
python generate_varied_puzzles.py
```

### Generating Storyline-Based Puzzles

To generate puzzles based on the game's narrative:

```bash
python generate_storyline_puzzles.py
```

### Analyzing and Sorting Puzzles

To analyze the puzzles and sort them properly by calculated difficulty:

```bash
python analyze_difficulty.py
```

This will enrich each puzzle with difficulty metrics and sort them from easiest to hardest.

## Extending

To add more puzzles or languages:

1. Add new language definitions to `puzzles/languages.json`
2. Update the story chapters in `generate_storyline_puzzles.py` for the new language
3. Run the scripts to generate and analyze the new puzzle data

## Cryptogram Game Mechanics

In a cryptogram puzzle:
1. Each letter in the original text is replaced with a number
2. The player must figure out which number corresponds to which letter
3. The difficulty increases as texts use more unique letters and have less predictable letter patterns

Players can use letter frequency analysis, common letter patterns, and word structure to solve the puzzles.
