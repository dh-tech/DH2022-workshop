# Data

- `bible-web.xml` "source document":
	- given to participants for annotation of persons and places in Recogito (to be tested)
	  [tbc: this is CES, not TEI, is the bible by Malte in TEI proper?]
 	- participants should perform manual annotations => JSON-LD standoff over the original TEI
 	- Note: couldn't be loaded with Recogito, use plain text, instead
 		- this failed because of a missing dtd: `/mnt/data/home/pelagios/recogito2/target/cesDoc.dtd (No such file or directory)` [unsurprisingly, because I uploaded the file only]
 		- => let's use plain text input instead of TEI
- `bible-web.txt` "source document":
	- extracted from `bible-web.conll`(see below) using

		cut -f 1  bible-web.conll | perl -pe "s/^\s*\n/<br>/g; s/\s+/ /g; s/<br>/\n/g;" | sed s/'  *'/' '/g > bible-web.txt
	
	- note: this has the additional advantage that the tokenization in this file and in the conll file is identical
 	- participants should perform manual annotations => JSON-LD standoff over the original text
 	- TODO: provide a script to export this as RDF
- `recogito-out/` output of manual annotation in Recogito
	- supports export as CSV, JSON-LD, TTL and RDF/XML
	- the TTL export seems to be incomplete, so work with the JSON-LD export
- `bible-web.conll` automated NER annotation, use to illustrate how to work with large-scale manually annotated data
	- annotated using [SENNA](https://ronan.collobert.com/senna/) (old but fast)
	- **question**: output format?
- `bible-web.ttl` (TODO): format to host *both* manual Recogito annotations over `bible-web.xml` and automated NER annotations from `bible-web.conll` in a uniform way
	- TODO(@Malte?): converter from Recogito+bible-web.xml (using Python?)
	- TODO(@Christian): converter from CoNLL (using [CoNLL-RDF](https://github.com/acoli-repo/conll-rdf)+SPARQL)
- next step: consume with Protégé (web protégé?)
	- manual refinement
