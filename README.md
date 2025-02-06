# comicgen
a fork of iopred's comicgen repo containing the directories, sprite sheets, and .json files necessary to run it locally.

## setup
### installation
one option is to download [Miniconda](https://docs.anaconda.com/miniconda/) and use the following commands in Anaconda Prompt:

```
git clone https://github.com/nice-frogboy/comicgen.git
cd comicgen
conda create --name comicgen --file requirements.txt
conda activate comicgen
```

then install the Go dependencies:

```
go get github.com/iopred/comicgen
```

### emojis
the 'emoji/google' directory should contain [128 x 128 google emojis in .png format](https://github.com/googlefonts/noto-emoji/tree/main/png/128). the 'emoji/twitter' directory should contain [72 x 72 twitter emojis in .png format](https://github.com/eallion/twemoji/tree/main/full/v/13.0.1/72x72).

### sprites
the 'characters' directory should contain sprite sheets each called '{character}.png' that consist of a single row of 161 x 230 pixel sprite tiles. the leftmost tile (0) contains a 32 x 32 thumbnail for the character at the top left. the remaining tiles are numbered (1), (2), and so on, from left to right. a single tile should contain a single sprite.

sample sprite sheets for the Microsoft Comics Chat roster are included, with 3 px of clearance from the bottom of the sprite tile, and a 2 px white border around the sprite.

### jsons
the 'characters' directory should contain files named '{character}.json' with dictionaries determining which sprites are pulled for each 'emotion'. if we want a character to use (1) and (3) when scared, we'd have our '{character}.json':

```
{
  "scared": [1, 3],
}
```

.json files for the Microsoft Comics Chat roster are included, but assignment is ambiguous, since this list of emotions is different from Microsoft Comics Chat.

## make a comic
an example comic, 'comic.png', can be created in the main directory with the following command:

```
go run cmd/comicgen/main.go
```

custom comics can be created either by modifying the main.go file, or creating and running other .go files based on main.go.
