# Curse of Ashenveil: A Text RPG with GPT-2

Something I did in my freetime when I was bored.....

A text-based fantasy RPG in Python where GPT-2 writes the scene descriptions on the fly. The game itself (combat, inventory, branching story) is regular Python logic, and GPT-2 supplies the narration, so every playthrough reads a little differently.

## Gameplay

You play a hero sent to break the curse over the village of Ashenveil. The story runs through five scenes, with your choices shaping the path:

1. **Village gate:** each choice gives a different starting item
2. **Dark forest:** fight a wolf, trade gold for a weapon at a witch's shrine, or rest
3. **Blackstone Castle:** fight the guards, sneak in through the wall, or parley with a knight
4. **Throne room:** fight the Shadow Warden, negotiate, or spring a trap
5. **Final chapter:** GPT-2 writes the closing paragraph based on how you got there

Dying in any fight ends the game.

## Features

- **Turn-based combat** with attack, defend (halves incoming damage), and use-item actions, plus random damage variance
- **Inventory and equipment:** seven items across weapons, armor, and consumables, with automatic equipping that updates your attack and defense
- **Status effects:** the Poison Dagger poisons enemies for damage over time
- **Branching story:** earlier choices change the next scene's prompt, the items you hold, and the options available
- **Input handling:** menu prompts keep asking until you enter a valid number

## How GPT-2 is used

The `generate_text` function sends a prompt to GPT-2 through Hugging Face Transformers and returns only the newly generated text. Each scene builds its prompt from the story so far (the hero's name and the path taken), then samples a continuation with `temperature=0.9` and `top_k=50`. Scene descriptions are limited to 50 new tokens, and the ending uses 80.

GPT-2 only writes flavor text. It does not control game rules or story outcomes.

## Run it

```bash
pip install transformers torch
```

Open `[notebook-name].ipynb` (or run `[script-name].py`) and run all cells. The GPT-2 model downloads automatically the first time you run it.

## Tools

Python, Hugging Face Transformers, PyTorch

## Author

Dean Chaudhry
