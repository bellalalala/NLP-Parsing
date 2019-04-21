# NLP-Parsing
For sentences containing 50 words or less (punctuation does not count), obtain the part-ofspeech tags, the context-free phrase structure grammar representation, and the typed dependency representation.

README
Q1
Preprocessing the input file:
Unzip the input folder: "corpus" under the same directory as the code.
Read files first；

Use stanford NLP parser to do pos tagging and generate parser:

Use the python package on
https://github.com/Lynten/stanford-corenlp/

First, install the package: 
pip install stanfordcorenlp;
Then, run following codes:
from stanfordcorenlp import StanfordCoreNLP
nlp = StanfordCoreNLP(r'stanford-corenlp-full-2018-10-05', memory='8g') 
After the above step we can use the package.

Split sentence using following code in the package:
props={'annotators': 'ssplit','pipelineLanguage':'en','outputFormat':'json'}
nlp.annotate(value, properties=props)
The output would be in format: dict{filename1:[sentence 1, sentence2,...], filename2:[sentence 1, sentence2,...],...}

Remove punctuations, multiple spaces so that we can count words correctly;
Count the words of each sentence and save them in the same format: dict{filename1:[#words of sentence 1, #words of sentence2,...], filename2:[#words of sentence 1, #words of sentence2,...],...}
For each sentence with words count <= 50, keep it in the corpus_rdtu with format: dict{filename1:[sentence 1, sentence2,...], filename2:[sentence 1, sentence2,...],...}

Generate the pos_tag, Constituency Parsing and Dependency Parsing raw files using the package. **This step need around 45 mins. Also generate the token using the package for latter usage.
** remember to close the nlp.

Save intermediate data for latter uasge.

The format of the output is different from the required format. Run the convert codes to convert the format as required. 
Generate a new folder named output under the same directory and save the output files in the output folder.

Q1.1 
Use the intermediate file pos_tag.pkl which is in the original format.
Count the total number of verbs and the number of sentence. The average number of verbs each sentence is 3.6505163928744713.

Q1.2
Use the intermediate file d_parsing.pkl which is in the original format.
Count the number of 'ROOT' in the total corpus.

Q1.3
After look into the output file, all the preposition are with tag 'case'. 
Use the intermediate file d_parsing.pkl and tkn'pkl which are of  the original format.
Count the number of 'case' which is the number of prepositions in each file.
For each preposition, count its number. And the most frequent 3 ones are: of, in, and to.
