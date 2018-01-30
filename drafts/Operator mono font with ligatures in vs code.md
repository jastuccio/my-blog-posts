# Add programming ligatures to Operator Mono!

https://github.com/kiliman/operator-mono-lig

You must own Operator Mono font


goto the command line:
* `$ pip install fonttools`
* `$ cd ~/Library/Fonts`
* `$ git clone https://github.com/kiliman/operator-mono-lig.git`
* `$ cp ~/Library/Fonts/OperatorMono* ~/Library/Fonts/operator-mono-lig/original`
* `$ cd operator-mono-lig`
* `$ ./build.sh`


-----

open VS Code:

"apple key" "comma key" to open VS Code settings

add the settings
"editor.fontFamily": "Operator Mono Lig",

Add a setting:
"editor.fontWeight": 400

100 - Thin
200 - Extra Light, Ultra Light
300 - Light
400 - Normal, Book, Regular
500 - Medium
600 - Semi Bold, Demi Bold
700 - Bold
800 - Extra Bold, Ultra Bold
900 - Black, Heavy

"editor.fontLigatures": true

