# comicgen
a fork of iopred's comicgen repo containing the directories, sprite sheets, and .json files necessary to run it locally.

# setup
one option is to download Miniconda (https://docs.anaconda.com/miniconda/) and use the following commands in Anaconda Prompt.

"""
git clone https://github.com/nice-frogboy/comicgen.git
cd comicgen
conda create --name comicgen --file requirements.txt
conda activate comicgen
"""

then install Go dependencies with:

"""
go get github.com/iopred/comicgen
"""

# emojis
the emoji/google directory should contain all the 128 x 128 google emojis in .png format (https://github.com/googlefonts/noto-emoji/tree/main/png/128).
the emoji/twitter directory should contain all the 72 x 72 twitter emojis in .png format (https://github.com/eallion/twemoji/tree/main/full/v/13.0.1/72x72).

# sprites
the characters/ directory must contain sprite sheets in the form <character_name>.png as a single row of 230 x  161 tiles. the leftmost tile does not contain
a sprite, but a 32 x 32 thumbnail for the character at the top left. the remaining tiles are sprites numbered 1, 2, 3, etc. sprite sheets for the original character
roster in Microsoft Comics Chat are included.

# jsons
the characters/ directory must contain a .json file for each character in the form <character_name>.json that contains a dictionary of emotions against lists of sprite
numbers. for instance, to use sprites 1 and 3 when 'scared':

"""
{
  "scared": [1, 3],
}
"""

.json files for the Microsoft Comics Chat character roster are included, but since the emotions here are not the same as in Microsoft Comics Chat, it's a little
ambiguous how these should be set up.

# run
a test comic, 'comic.png', can be created in the main directory with the following command:

"""
go run cmd/comicgen/main.go
"""

custom comics can be created by modifying main.go or creating other .go files using main.go as a template.