# Masked Language Model Using BERT

## Overview
This project implements a Masked Language Model using BERT, a transformer-based model developed by Google, to predict masked words in text sequences. It also generates attention visualizations to help analyze what BERT’s attention heads are paying attention to as it processes text. By leveraging the `transformers` Python library from Hugging Face, this project demonstrates the power of modern NLP models for understanding language patterns.

## Example Outputs:
```bash
python mask.py
Text: We turned down a narrow lane and passed through a small [MASK].
We turned down a narrow lane and passed through a small field.
We turned down a narrow lane and passed through a small clearing.
We turned down a narrow lane and passed through a small park.

$ python mask.py
Text: Then I picked up a [MASK] from the table.
Then I picked up a book from the table.
Then I picked up a bottle from the table.
Then I picked up a plate from the table
```

## Project Structure
1. **Masked Word Prediction:**  
   The model takes user input in the form of a sentence with a masked word (represented by the `[MASK]` token) and predicts the most probable words to replace the mask using BERT.

2. **Attention Visualization:**  
   The project generates visual representations of the attention scores from each of BERT's 144 attention heads (12 layers with 12 heads each). These visualizations offer insights into the patterns BERT has learned to focus on while processing language.

## Key Functions
### 1. `get_mask_token_index`
   - Finds the index of the `[MASK]` token within the input sequence.
   - Returns the 0-indexed position of the token, or `None` if no mask is present.

### 2. `get_color_for_attention_score`
   - Maps an attention score (between 0 and 1) to an RGB value.
   - Outputs a shade of gray, where 0 is black `(0, 0, 0)` and 1 is white `(255, 255, 255)`, and intermediate values result in appropriate shades of gray.

### 3. `visualize_attentions`
   - Generates attention diagrams for each attention head in every layer.
   - Uses the `generate_diagram` function to produce visualizations for analysis, providing insights into BERT’s behavior across different attention heads.

## How It Works
1. **Tokenization:**  
   The input text is tokenized using the BERT tokenizer. Special tokens like `[MASK]`, `[CLS]`, and `[SEP]` are added to structure the sequence.

2. **Prediction:**  
   The BERT model predicts the most likely candidates for the masked word by analyzing the surrounding context. It uses 144 attention heads spread across 12 transformer layers.

3. **Visualization:**  
   The attention visualizations provide a heatmap of attention scores between tokens. This allows us to interpret which tokens in a sentence are receiving the most attention from BERT as it tries to understand the sentence.

## Analysis of Attention Heads
Part of the project involves analyzing attention heads to infer relationships between words. For example, Layer 3, Head 10 tends to focus on the next word in the sequence, while other heads may focus on different grammatical relationships like verb-object pairs.

In the `analysis.md`, you'll be tasked with exploring new attention head patterns and providing examples of what these attention heads seem to be paying attention to.

## Setup and Usage
1. **Installation**:
   Clone the repo using `git clone https://github.com/musty-ess/Masked-Language-Model-Using-BERT.git` and run the following to install dependencies: `pip install -r requirements.txt`
2. **Running the Model**: 
   To predict a masked word, run `python mask.py`
3. **Requirements**:
- Python 3.12
- Hugging Face transformers library
- TensorFlow
