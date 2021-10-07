# question

1. code

   spacy = 2.1.0 

   ne = source 

   ```
   import spacynlp = spacy.load('en_core_web_sm')# load NeuralCoref and add it to the pipe of SpaCy's modelimport neuralcorefcoref = neuralcoref.NeuralCoref(nlp.vocab)nlp.add_pipe(coref, name='neuralcoref')# You're done. You can now use NeuralCoref the same way you usually manipulate a SpaCy document and it's annotations.doc = nlp(u'My sister has a dog. She loves him.')print(doc._.has_coref,doc._.coref_clusters)
   ```

   ```
   B:\当前任务\Science_Fiction\Spacy_entity\.env2\Scripts\python.exe B:/当前任务/Science_Fiction/Spacy_entity/test_spacy.py
   Traceback (most recent call last):
     File "B:/当前任务/Science_Fiction/Spacy_entity/test_spacy.py", line 4, in <module>
       import neuralcoref
     File "b:\当前任务\science_fiction\spacy_entity\.env2\neuralcoref\neuralcoref\__init__.py", line 10, in <module>
       from neuralcoref.neuralcoref import NeuralCoref
     File "span.pxd", line 7, in init neuralcoref.neuralcoref
   ValueError: spacy.tokens.span.Span size changed, may indicate binary incompatibility. Expected 80 from C header, got 72 from PyObject
   ```

   

2. d

3. d

4. 



