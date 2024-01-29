<!-- ABOUT THE PROJECT -->
## ConEC: Earnings Call Dataset with Real-world Contexts for Benchmarking Contextual Speech Recognition

Earnings calls are are events where publicly traded companies communicate their financial performance and results to investors, analysts, and the general public. These calls typically take place on a quarterly basis, following the release of a company's quarterly financial statements. These calls are often recorded and made publicly available through the company's website or financial news services ([an example](https://ir.aboutamazon.com/quarterly-results/default.aspx)). Many companies accompany their earnings calls with presentation slides and press releases to provide additional context, visual aids, and concise summaries of their financial results.

Can these contexts help machines better recognizing and understanding the earnings calls?

In this project, we augment [Earnings-21/22](https://github.com/revdotcom/speech-datasets/tree/main) corpus by correcting their transcription and associating each earnings call with its contexts, including presentation slides, earnings news release as well as a list of meeting participants' names and affiliations. All our data are public (e.g., downloaded from the companies website), as opposed to [other financial databases](https://faq.library.upenn.edu/business/faq/45579#:~:text=Where%20available%2C%20they%20also%20provide%20access%20to%20the%20Powerpoint%20presentations%20that%20accompany%20the%20conference%20calls%2C%20as%20well%20as%20audio%20files.) which are not available to many researchers.

In particular, we also provide baselines in [icefall](https://github.com/k2-fsa/icefall/tree/master/icefall) toolkit for contextualized ASR, where we hope to improve the speech recognition of context-specific vocabulary and named entities, such as the names of companies, products, events and people, which are hard for conventional ASR to recognize correctly.

### Cite this dataset

```
To be filled
```

### Directory and format

```
ConEC
├── earnings21
│   ├── contexts
│   │   ├── *.txt
│   │   ├── participant_names
│   │   └── pdfs
│   └── transcripts
│       ├── nlp_references
│       ├── timestamps
│       ├── wer_tags
│       └── fixed_potential_errors_log
├── earnings22
│   ├── contexts
│   │   ├── participant_names
│   │   └── pdfs
│   └── transcripts
└── README
```

For earnings21/22 subsets, each contains the following directories:

#### contexts:

* `pdfs`: This directory contains presentation slides and press release for each earnings call in PDF format. They can be parsed by tools such as [pdftotext](https://github.com/jalan/pdftotext).
* `participant_names`: The names and affiliation information of the earnings calls participants are usually known in advance. For example, companies often provide a mechanism for participating analysts and investors to register or submit questions ahead of time. We collect such information from [seekingalpha](https://seekingalpha.com/).
* `*.txt`: these are the biasing word lists that we have extracted from the PDF files, with stop words, numerical values and irrelevant pages (e.g., the slides containing "forward-looking statement") removed. The participant names and affliations are also added to the lists.

#### transcripts:

We follow the "*.nlp" [file format](https://github.com/revdotcom/speech-datasets/tree/main/earnings21#file-format-overview) as defined in the earnings21/22 corpus, and release a corrected version of the transcription. Indeed, transcribing earnings calls containing many unfamiliar names and jargons can be a hard task even for human beings! We noticed several issues in the original  earnings21/22 transcription: (1) Some named entities are transcribed as [\<unk\>](https://github.com/revdotcom/speech-datasets/blob/main/earnings21/transcripts/nlp_references/4367535.nlp#L4033) or [\<inaudible\>](https://github.com/revdotcom/speech-datasets/blob/main/earnings21/transcripts/nlp_references/4367535.nlp#L4035); (2) Some named entities are transcribed as homophones or closely rhyming words, e.g., Piotr vs. Petro, which does not align with real-world facts; (3) Some other [mistakes](https://github.com/revdotcom/speech-datasets/blob/main/earnings21/transcripts/nlp_references/4341191.nlp#L10877) in the corpus.

* `nlp_references`: This directory contains the updated nlp files, which is supposed to replace the original nlp files in earnings21/22 repository.
* `timestamps`: This directory augments the updated nlp files with automatic aligned word-level timestamps.
* `wer_tags`: This directory contains the updated wer_tags files, which is supposed to replace the original wer_tag files in earnings21/22 repository.
* `fixed_potential_errors_log`: Here are the log files for our semi-automatic transcription correction process.

### Support and contact information

blah blah blah
