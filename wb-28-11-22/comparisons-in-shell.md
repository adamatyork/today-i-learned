# Monday 28th November 2022

**Today I Learned**
<br>

In `Shell`, comparisons are made with conditional operators. <br>
Unlike most languages, you don't compare objects with `==` or `!=` etc. <br>

Here are the most common comparisons in Shell and C# format. <br><br>

Comparison | C# | Shell 
-- | -- | --
Equal | == | -eq
No Equal | != | -ne
Less Than | < | -lt
Less Than or Equal | <= | -le
Greater Than | > | -gt
Greater Than or Equal | >= | -ge

<br>

For example to compare two number variables... <br>

```bash
if [MY_NUMBER -ne 3]
then
    echo "It's not three!"
fi
```

Different operators are used for different types, however. Eg strings... <br>


```bash
if [MY_STRING="Yolo"] 
then 
    echo "Woo! Yolo!"
fi
```


<br>
<br>

## Ref. Links. Etc.
[Tutorial](https://www.digitalocean.com/community/tutorials/if-else-in-shell-scripts) <br>
[StackOverflow](https://stackoverflow.com/questions/10849297/compare-a-string-using-sh-shell) <br>
