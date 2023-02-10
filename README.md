# Okse Wallet Assets Info

![Check](https://github.com/trustwallet/assets/workflows/Check/badge.svg)

## Overview

Okse Wallet token repository is a comprehensive, up-to-date collection of information about several thousands (!) of crypto tokens.

[Okse Wallet](https://okse.io) uses token logos from this source, alongside a number of other projects.

The repository contains token info from several blockchains, info on dApps, staking validators, etc.
For every token a logo and optional additional information is available (such data is not available on-chain).

Such a large collection can be maintained only through a community effort, so _feel free to add your token_.

<center><img src='https://okse.io/images/logo.png' height="100"></center>

## How to add token

Please note that __brand new tokens are not accepted__,
the projects have to be sound, with information available, and __non-minimal circulation__
(for limit details see <https://docs.okse.io/developers/assets/requirements>).


### To Add Logo

- [ ] Fork the Github repository

- [ ] Create folder with name of token smartcontact address in **CHECKSUM** format `blockchains/ethereum/assets/<token_smartcontract_address>/`.

- [ ] Tell your designer that token image must be in PNG format, avoid transparent background, recommended size 256x256px, with max file size of 100kB.

- [ ] Upload your logo with file named `logo.png` to previously created folder with smartcontract address, and if you done all correctly your path should look like this. `blockchains/ethereum/assets/0x1234567461d3f8Db7496581774Bd869C83D51c93/logo.png`

- [ ] Run `npm run check` and make sure tests pass

- [ ] Create a pull request to the main repo


## Scripts

There are several scripts available for maintainers:

- `make check` -- Execute validation checks; also used in continuous integration.
- `make fix` -- Perform automatic fixes where possible
- `make update-auto` -- Run automatic updates from external sources, executed regularly (GitHub action)
- `make add-token asset_id=c60_t0x4Fabb145d64652a948d72533023f6E7A623C7C53` -- Create `info.json` file as asset template.
- `make add-tokenlist asset_id=c60_t0x4Fabb145d64652a948d72533023f6E7A623C7C53` -- Adds a token to tokenlist.json.
- `make add-tokenlist-extended asset_id=c60_t0x4Fabb145d64652a948d72533023f6E7A623C7C53` -- Adds a token to tokenlist-extended.json.

## On Checks

This repo contains a set of scripts for verification of all the information. Implemented as Golang scripts, available through `make check`, and executed in CI build; checks the whole repo.
There are similar check logic implemented:

- in assets-management app; for checking changed token files in PRs, or when creating a PR.  Checks diffs, can be run from browser environment.
- in merge-fee-bot, which runs as a GitHub app shows result in PR comment. Executes in a non-browser environment.

## Trading pair maintenance

Info on supported trading pairs are stored in `tokenlist.json` files.
Trading pairs can be updated --
from Uniswap/Ethereum and PancakeSwap/Smartchain -- using update script (and checking in changes).
Minimal limit values for trading pair inclusion are set in the [config file](https://github.com/Okseio/assets/blob/master/.github/assets.config.yaml).
There are also options for force-include and force-exclude in the config.


