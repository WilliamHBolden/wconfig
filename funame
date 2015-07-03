#!/bin/bash

red='\033[0;31m'
NC='\033[0m'

nlist="/afs/cats.ucsc.edu/users/k/wbolden/public/data/users/nlist"

if [[ $* == *-x* ]]; then
    exclusive=true
    firstitem=$2
    shift;
fi

if [[ "$exclusive" = true ]]; then

    if [[ $# -eq 1 ]]; then
	ret=$(grep -iw --color=always "\s$1\s" $nlist.bak)
    elif [[ $# -eq 2 ]]; then
	ret=$(grep -iw --color=always "\s$1".*"\s$2" $nlist.bak)
    elif [[ $# -eq 3 ]]; then
	ret=$(grep -iw --color=always "\s$1".*"\s$2".*"\s$3" $nlist.bak)
    else
	ret=$(grep -iw --color=always "\s$1".*"\s$2".*"\s$3".*"\s$4" $nlist.bak)
    fi
else
    if [[ $# -eq 1 ]]; then
	ret=$(grep -i --color=always "\s$1" $nlist.bak)
    elif [[ $# -eq 2 ]]; then
	ret=$(grep -i --color=always "\s$1".*"\s$2" $nlist.bak)
    elif [[ $# -eq 3 ]]; then
	ret=$(grep -i --color=always "\s$1".*"\s$2".*"\s$3" $nlist.bak)
    else
	ret=$(grep -i --color=always "\s$1".*"\s$2".*"\s$3".*"$4" $nlist.bak)
    fi
fi
num=$(echo "$ret" | wc -l)

if [ -z "$ret" ]
then
    echo -e Found "${red}"0"${NC}" matches
else
    if [ $num -eq 1 ]
    then
	echo -e Found "${red}"$num"${NC}" match
	echo "$ret"
    else
	echo -e Found "${red}"$num"${NC}" matches
	echo "$ret"
    fi
fi


