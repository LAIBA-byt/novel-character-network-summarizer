StoryGraph: Novel Character Network & Story Summarizer

An NLP and network analysis project that extracts characters from a novel, builds a character relationship network, and generates an abstractive summary of a story passage.

The demo uses Alice's Adventures in Wonderland (Project Gutenberg).
Features
Character extraction: finds PERSON entities with spaCy Named Entity Recognition and shortlists the most frequent characters.
Co-occurrence network: two characters appearing in the same sentence are connected by an edge. The edge weight grows with how often they appear together.
Interactive visualization: the network is shown as a zoomable, draggable HTML graph (PyVis), with a static Matplotlib plot as well.
Abstractive summarization: a passage from the novel is summarized with the pre-trained BART model (facebook/bart-large-cnn).
Tech Stack
Purpose	Tool
Language	Python
NER	spaCy (en_core_web_sm)
Graph analysis	NetworkX
Visualization	PyVis, Matplotlib
Summarization	Hugging Face Transformers (BART)
Environment	Google Colab / VS Code
How It Works
Load text: the novel is loaded from a Project Gutenberg text file.
NER: spaCy extracts PERSON entities, and collections.Counter ranks the top characters.
Graph building: for each sentence, every pair of top characters found together gets an edge in an nx.Graph(), and the weight is incremented on repeats.
Visualization: the graph is exported to an interactive HTML file with PyVis.
Summarization: a text segment is passed to BART to generate a short summary.
Installation
bash
git clone https://github.com/LAIBA-byt/<repo-name>.git
cd <repo-name>
pip install spacy networkx pyvis matplotlib transformers torch
python -m spacy download en_core_web_sm
Usage

Open the notebook in Google Colab or VS Code and run the cells in order. The interactive graph is saved as an .html file (for example character_network.html). Open it in any browser.
Sample Output
Top characters found: Alice, Mouse, Bill, William, Mabel, Mary Ann, Duck, Edwin, Mercia, Caucus
Add a screenshot of the network graph here: ![Character Network](images/network.png)
Add the generated summary here.
Limitations
NER runs on only the first 50,000 characters of the text, so the network does not cover the whole novel.
Summarization is done on a single segment (text[1000:4000]), not the full book.
spaCy's small model sometimes mislabels non-character words as PERSON (for example, "Caucus" is a race, not a character).
The same character may appear under different names (for example, "Mary Ann").
BART is used as-is (pre-trained, no fine-tuning).
Future Improvements
Process the full novel in chunks.
Merge name variants into one character (entity resolution).
Chunk-wise summarization of the entire book.
Use a larger spaCy model for better NER accuracy.
Author

Laiba Afzal, BS Software Engineering, University of Okara GitHub: LAIBA-byt
