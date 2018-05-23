# Lagomorpha

Initial experiments and recipes for working with Latin and Greek morphology, based on [code libraries by Neel Smith](https://github.com/neelsmith?tab=repositories).

## Steps

1. Get into a REPL

    `sbt console`
    `:load scripts/utils.sc`

1. Select a sub-corpus (one poem)

	`val ode37:Corpus = repo.corpus ~~ CtsUrn("urn:cts:latinLit:phi0893.phi001.fulat1:1.37")`

1. Validate orthography of selected sub-corpus and tokenize

	`val ode37AllTokens = tokenize(ode37)`

1. Select lexical tokens.

	`val histo1 = histo(ode37AllTokens)`
	`val justLexTokens = ode37AllTokens.filter(_.category == LexicalToken)`

1. Do histograms.

	`val histo1 = histo(ode37AllTokens)`
	`val histo2 = histo(justLexTokens)`
	`val histo3 = histo(ode37AllTokens,Some(LexicalToken))`

1. Convert to sequence to see frequencies

	`histo3.toSeq.sortBy(_._2).reverse`