---
layout: post
title: Modify a JSON in cli
tags: [json]
author: klex
---

[Source: Monsanto](http://engineering.monsanto.com/2015/05/22/jq-change-json/)

# Modify a speficic key in a JSON

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
