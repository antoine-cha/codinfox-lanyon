---
layout: post
title: custom-auto-completion.md
author: Klexounet
tags: [Klexounet,bash]
---
# Custom auto-completion for bash functions

First, create a bash function (in `.bash_aliases` or `.bashrc`).
```bash
# Attach a docker container with a new bash, with completion
docker-new-bash(){
    docker exec -t -i $1 /bin/bash
}
```
## Custom autocompletion from a list of words
```bash
complete -W "coucou pouet" docker-new-bash
```

Outputs when tabbing
```
alexandre@father03:~$ docker-new-bash [tab]
coucou  pouet
```

## Custom autocompletion from a bash function

Auto-completion proposals are in `COMPREPLY` array
```bash
_docker-new-bash(){
    COMPREPLY=("coucou" "pouet")
}
complete -F _docker-new-bash docker-new-bash
```

Outputs when tabbing
```
alexandre@father03:~$ docker-new-bash [tab]
coucou  pouet
```

## Copy the autocompletion of another bash function

```bash
# Copy autocompletion from other function
get_completions(){
    local completion COMP_CWORD COMP_LINE COMP_POINT COMP_WORDS COMPREPLY=()
    # load bash-completion if necessary
    declare -F _completion_loader &>/dev/null || {
        source /usr/share/bash-completion/bash_completion
    }
    COMP_LINE=$*
    COMP_POINT=${#COMP_LINE}
    eval set -- "$@"
    COMP_WORDS=("$@")
    # add '' to COMP_WORDS if the last character of the command line is a space
    [[ ${COMP_LINE[@]: -1} = ' ' ]] && COMP_WORDS+=('')
    # index of the last word
    COMP_CWORD=$(( ${#COMP_WORDS[@]} - 1 ))
    # determine completion function
    completion=$(complete -p "$1" 2>/dev/null | awk '{print $(NF-1)}')
    # run _completion_loader only if necessary
    [[ -n $completion ]] || {
        # load completion
        _completion_loader "$1"
        # detect completion
        completion=$(complete -p "$1" 2>/dev/null | awk '{print $(NF-1)}')
    }
    # ensure completion was detected
    [[ -n $completion ]] || return 1
    # execute completion function
    "$completion"
    # Return array of completions
    echo "${COMPREPLY[@]}"
}

_docker-new-bash(){
    local cur=${COMP_WORDS[COMP_CWORD]}
    local comp=$(get_completions 'docker attach ')
    COMPREPLY=( $(compgen -W "$comp" -- $cur) )
}
complete -F _docker-new-bash docker-new-bash
```

Outputs when tabbing
```
alexandre@father03:~$ docker-new-bash [tab]
vod_product_compute vod_product_mysql
alexandre@father03:~$ docker attach [tab]
vod_product_compute vod_product_mysql
```
