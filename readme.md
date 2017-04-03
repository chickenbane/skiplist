# Let's implement a skiplist

http://ticki.github.io/blog/skip-lists-done-right/

```
-- Recursive skip list insertion function.
define insert(elem, root, height, level):
    if right of root < elem:
        -- If right isn't "overshot" (i.e. we are going to long), we go right.
        return insert(elem, right of root, height, level)
    else:
        if level = 0:
            -- We're at bottom level and the right node is overshot, hence
            -- we've reached our goal, so we insert the node inbetween root
            -- and the node next to root.
            old ← right of root
            right of root ← elem
            right of elem ← old
        else:
            if level ≤ height:
                -- Our level is below the height, hence we need to insert a
                -- link before we go on.
                old ← right of root
                right of root ← elem
                right of elem ← old

            -- Go a level down.
            return insert(elem, below root, height, level - 1)
```


* add .gitignore
* Tools -> Kotlin -> Configure Kotlin in Project
