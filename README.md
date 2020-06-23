# blockchain-analyzer

[![CircleCI](https://circleci.com/gh/danhper/blockchain-analyzer.svg?style=svg)](https://circleci.com/gh/danhper/blockchain-analyzer)

CLI tool to fetch and analyze transactions data from multiple blockchains.

Currently supported blockchains:

* [Tezos](https://tezos.com/)
* [EOS](https://eos.io/)
* [XRP](https://ripple.com/xrp/)

## Installation

### Static binaries

We provide static binaries for Windows, macOS and Linux with each [release](https://github.com/danhper/blockchain-analyzer/releases)

### From source

Go needs to be installed. The tool can then be installed by running

```
go get github.com/danhper/blockchain-analyzer/cmd/blockchain-analyzer
```

## Usage

### Fetching data

The `fetch` command can be used to fetch the data:

```
blockchain-analyzer BLOCKCHAIN fetch -o OUTPUT_FILE --start START_BLOCK --end END_BLOCK

# examples
blockchain-analyzer eos fetch -o eos-blocks.jsonl --start 500000 --end 600000
```

The `check` command can then be used to check the fetched data.

```
blockchain-analyzer eos check -p 'eos-blocks*.jsonl' -o missing.jsonl --start 500000 --end 600000
```


### Analyzing data

The simplest way to analyze the data is to provide a configuration file about what to analyze and run the tool with the following command.

```
blockchain-analyzer <tezos|eos|xrp> bulk-process -c config.json -o tmp/results.json
```

Configuration files used for [our paper](https://arxiv.org/abs/2003.02693) can be found in the [config](./config) directory.

The tool's help also contains information about what other commands can be used


```
blockchain-analyzer -h
```


### Academic work

This tool has originally been created to analyze data for the following paper: [Revisiting Transactional Statistics of High-scalability Blockchain](https://arxiv.org/abs/2003.02693).  
If you are using this for academic work, we would be thankful if you could cite it.

```
@misc{perez2020revisiting,
    title={Revisiting Transactional Statistics of High-scalability Blockchain},
    author={Daniel Perez and Jiahua Xu and Benjamin Livshits},
    year={2020},
    eprint={2003.02693},
    archivePrefix={arXiv},
    primaryClass={cs.CR}
}
```
