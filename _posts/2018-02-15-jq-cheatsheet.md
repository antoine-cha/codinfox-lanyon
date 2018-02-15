---
layout: post
title: JQ cheatsheet
tags: [json]
author: klex
---

[Source: Monsanto](http://engineering.monsanto.com/2015/05/22/jq-change-json/)

## Add/change a key to a JSON

```bash
function jq_add_key {
  jq --arg key "$2" ". + {$2: \$key}"
}

cat <source>.json | jq --arg key <value> '. + {<key>: $key}'

cat {source}.json | jq_change_key {key} {new_value} > {dest}.json

```

## Modify a key only if exists in a JSON

```bash
function jq_change_key {
    jq "to_entries |
        map(if .key == \"$1\"
            then . + {\"value\":\"$2\"}
            else .
            end) |
        from_entries"
}                                      

cat {source}.json | jq_change_key {key} {new_value} > {dest}.json
```

*Caution:* do not replace `{source}.json` as you `cat` it, it would result in a blank file !
