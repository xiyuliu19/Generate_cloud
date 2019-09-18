# Generate_cloud
mkdir Generate_cloud<br>
vi generate_cloud.sh<br>
```Bash
#!/bin/bash
#
#
if [ "$1" = "" ]; then
   echo "   Quick Help: Welcome to my program for creating a word cloud! You see this message bacause you run this program with no arguments. This message is about how to use this program.

In the first step, if you want to make a wordcloud, you should pick some terms that you interest and input them when you run this program.
For example, you pick the term of bioinformatics, you should run this program in this way: ./generate_cloud.sh -- bioinformatics
If you pick more than one term, you should separate each term with a comma in this way: ./generate_cloud.sh -- biomedical,informatics

In the second step, you need to choose the font color for your wordcloud picture. You should type the color name after the terms using a space to seperate it with the term argument.
For example, you want red font, you can run like this: ./generate_cloud.sh -- biomedical,informatics red

In the third step, you need to choose the background color for your wordcloud picture. You should type the color name for the background after the font color both using a space to seperate it with the font color argument.
For example, you want black background, you can run like this: ./generate_cloud.sh -- biomedical,informatics red black

Now, you get your wordcloud picture. You can see a file called generate_cloud.txt and a picture called wordcloud.png in your list.

Conguatulations! You can download it to your computer now!"
exit;
fi
```
#This step is to meet the requirement that if the user just run the program by "./generate_cloud.sh"<br>
#Because there are no arguments it should provide a `quick help`<br>

```Bash
ARGUMENTS=`getopt -o tcb: --long term,color,background: -n 'parse-options' -- "$@"`
eval set -- "$ARGUMENTS"
TERM=$2
COLOR=$3
BACKGROUND=$4

while true; do
case "$1" in
    -t | --term ) TERM=$2; shift ;;
    -c | --color )    COLOR=$3; shift ;;
    -b | --background ) BACKGROUND=$4; shift; shift ;;
    -- ) shift; break ;;
* ) break ;;
esac
done
echo TERM=$TERM
echo COLOR=$COLOR
echo BACKGROUND=$BACKGROUND

esearch -db pubmed -query "$TERM" |   efetch -format abstract > generate_cloud.txt
wordcloud_cli --text generate_cloud.txt --color "$COLOR" --background "$BACKGROUND" --imagefile wordcloud.png
```
#Then,I run this program several times to change the terms,font color, and background color<br>
#I create a lot of amazing wordcloud pictures by my generate_cloud program!<br>
