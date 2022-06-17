# Data

- `bible-web.xml` "source document":
	- given to participants for annotation of persons and places in Recogito (to be tested)
	  [tbc: this is CES, not TEI, is the bible by Malte in TEI proper?]
 	- participants should perform manual annotations => JSON-LD standoff over the original TEI
 	- Note: couldn't be loaded with Recogito, use plain text, instead
- `bible-web.txt` "source document":
	- extracted from `bible-web.conll`(see below) using

		cut -f 1  bible-web.conll | perl -pe "s/^\s*\n/<br>/g; s/\s+/ /g; s/<br>/\n/g;" | sed s/'  *'/' '/g > bible-web.txt
	
	- note: this has the additional advantage that the tokenization in this file and in the conll file is identical
 	- participants should perform manual annotations => JSON-LD standoff over the original text
 	- TODO: provide a script to export this as RDF
- `bible-web.conll` automated NER annotation, use to illustrate how to work with large-scale manually annotated data
	- annotated using [SENNA](https://ronan.collobert.com/senna/) (old but fast)
	- **question**: output format?
- `bible-web.ttl` (TODO): format to host *both* manual Recogito annotations over `bible-web.xml` and automated NER annotations from `bible-web.conll` in a uniform way
	- TODO(@Malte?): converter from Recogito+bible-web.xml (using Python?)
	- TODO(@Christian): converter from CoNLL (using [CoNLL-RDF](https://github.com/acoli-repo/conll-rdf)+SPARQL)
- next step: consume with Protégé (web protégé?)
	- manual refinement
	- NOTE: in addition to recogito information, we need rdfs:labels as orientation for manual re-structuring and search