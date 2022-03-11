[Index](https://jheidenr.github.io/cse15l-lab-reports)

# Lab Report 5

## Finding the Different Results

I found the different tests by copying the output of a bash loop into text files for both implementations. Then I used the `diff` command on both files to find the differences between them. Once I had the list of differences, I just picked a few from the top of the list.

## Test File 194

```
[Foo*bar\]]:my_(url) 'title (with parens)'
 
[Foo*bar\]]
```

Output For My Implementation:
[]

Output For the Given Implementation:
[url]

The given implementation is correct for this test file.

My implementation provides an incorrect output for this file because my code attempts to only provide valid links that could actually lead to a website. It checks the inside of the parentheses for common url tags. Since this test file has a non-link in the parentheses but the syntax is still correct, my code thinks that the link is invalid and outputs an empty list.

```
for (String s : validExtensions) {
    if (markdown.substring(openParen+1, closeParen).contains(s)) {
        toReturn.add(markdown.substring(openParen + 1, closeParen));
    }
}
```

As you can see from this block from my code, my program checks for valid link extensions from a pre determined list. I believe that simply removing the for loop would make my implementation work for this file.

## Test File 201

```
[foo]: <bar>(baz)
 
[foo]
```

Output For My Implementation:
[]

Output For the Given Implementation:
[baz]

My implementation is correct for this file.

The given implementation provides an incorrect output for this file because it does not check that the beginning parentheses is right next to the ending bracket in the file.

```
if(potentialLink.indexOf(" ") == -1 && potentialLink.indexOf("\n") == -1) {
    toReturn.add(potentialLink);
    currentIndex = closeParen + 1;
}
```

The block of code above is the location where a link is added to the list. An easy way to fix the code for this file would be to check the location of the parentheses with respect to the brackets, before adding a link to the list. This could be done by adding another internal if statement or just by adding more conditions to the existing if statement.