# nlpp-fmt

Text formatting tool for NLPP `*.xml` files (generated via [NLPTextTool](https://github.com/LovePlusProject/NLPTextTool)).

It exports simplified `*.txt` files for ease of translation, without the need to worry about formatting. These `*.txt` can be re-imported back into `*.xml` files, with automatic formatting (tag aliases, symbol replacement, word wrapping, etc).


## Setup

- Download and install [Python 3](https://www.python.org/downloads/). Make sure to check the "Add to PATH" option!
- Open up Command Prompt and run `pip install pyyaml`.
- Download [NLPTextTool](https://github.com/LovePlusProject/NLPTextTool).


## Usage

### Unpacking files

> Generating worksheets for translation work

- Export `*.dbin2` files from the game.
- Drag and drop one or more `*.dbin2` files on `NLPTextTool.exe` to create the `*.xml` dumps.
- Drag and drop one or more `*.xml` files on `process.cmd` to create the `*.txt` dumps.

**Note**: Keep the `*.dbin2`, `*.xml` and `*.txt` files in the same folder.


### Repacking files

> Reinserting translated worksheets

- Drag and drop one or more updated `*.txt` files on `process.cmd` to repack them into the `*.xml` files.
- Drag and drop one or more updated `*.xml` files on `NLPTextTool.exe` to repack them into the `*.dbin2` files.


### Merging files

> Generating multi-language worksheets

- Export the Japanese scripts into a folder named `00`.
- Export the translated scripts into a folder named `01`.
- Drag and drop both folders on `merge.cmd` a new folder named 'merged' will appear.

Text from the first set of files (`00`) will be commented out (with `//`). These lines will not be repacked.


#### Notes

Unpacking Japanese scripts:

- Set `render_new_lines` to `true` in the configuration file
- Set `comment_japanese` to `false` in the configuration file

Unpacking translated scripts:

- Set `render_new_lines` to `false` in the configuration file
- Set `comment_japanese` to `true` in the configuration file

To use the English translation as the reference scripts (to create a worksheet in another language), merge two copies of the English scripts together.
To format the Japanese scripts for a new translation worksheet, merge two copies of the Japanese scripts together.
To repack the merged `.txt` worksheets, place them in the same directory as the reference `*.xml` files.


## Configuration

The file <./config.yml> is a YAML file containing the configuration for the tool. The options are documented via the lines prefixed with `#` (comments).

**Note**: Lines requiring overrides (to skip reflowing or to handle multiple-choice options) have not been full populated into the config. They will be periodically added when discovered.
