# US and International phone number Regex

Introductory paragraph 
--------------------------------------
Today I will be demonstrating a common regex that can handle a variety of US based phone number variations as well as the common +1 international extension. The regex is helpful as with normal search queries in code, we are only able to use various functions such as .startswith(), endswith() or includes(). However if we require more powerful and flexible searching parameter then we can utilize regex for that purpose.


## Summary

/(\+1[ -])?\(?(\d{3})\)?[ -.]?(\d{3})[ -.]?(\d{4})/

Above is the code for the Regex, this was tested and made in regexr.com. This will allow the user to find the search parameters for any US and International based phone numbers when implemented.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
^((\+\d{1,2})[ -])?\(?(\d{3})\)?[ -.]?(\d{3})[ -.]?(\d{4})$
Above is the completed regex that can has the parameters to include spaces, periods and paranthesis.
There were other variations that were tested while learning about regex components such as

\d{10} - This regex would only search ror a string of digits ten long. A simple search that would return 1234567890

\d{3}-?\d{3}-?\d{4} - This regex would search for a string of 3 digits, then an optional dash. Followed by another 3 digits another dash (again optional), then finally 4 digits. This regex would be able to handle searching for 123456789 || 123-456-7890

\d{3}[ -.]?\d{3}[ -.]?\d{4} - This regex does as above but now will include a space as well as a dash for the search pattern, as well as a period. Result being 123456789 || 123-456-7890 || 123 456 7890 || 123.456.7890

\(?(\d{3})\)?[ -.]?(\d{3})[ -.]?(\d{4}) - This regex will now include a set of parenthesis around the area code. 

^((\+\d{1,2})[ -])? - This part of the regex handles the +1 search pattern as well as any number combination of +1 or +12. It can includ 1 or up to 2 numbers following the + sign.

### Anchors
We have the ^ anchor tag at the beginning to denote that we want to start our pattern with a +(12) so that we are able to include interntional phone numbers in our search, as well as a $ anchor at the end to ensure we end our search with looking for a series of 4 numbers. We include the optional ? to the search so that it can include US based numbers that do not include that beginning +12 search. Again the +12 is arbitrary and can be any number. 

### Quantifiers
\d{1,2}, \d{3}, \d{4}

These are various quantifiers that were included in the regex to allow us to narrow our search pattern. \d will narrow it to a set of digits, {1,2} will allow a range between 1 and 2. \d{3} searches for a pattern that is exactly 3. 


### Grouping and Capturing
We grouped our search pattern to denote how we want to search. \(?(\d{3})\)? This grouping here allows us to search for a pattern of 3 digits that may include a opening ( and a closing )

### Bracket Expressions

^((\+\d{1,2})[ -])?\(?(\d{3})\)?[ -.]?(\d{3})[ -.]?(\d{4})$

In our search pattern we also included [] "Bracket Notation" this allows us to represent a range of character or symbols that we wish to match in our search. I.e [abc] will look for a string that inclues a, b or c. Results could be "abc", "aaa", "cba". In our example we use it to include a space, a dash and a period in our search pattern for phone numbers. 

### Greedy and Lazy Match
On a regular search parameters we are looking for a straight match based on the regex. With the inclusion of the ? we are able to make certain grouping's an optional match as well. It will look for matches that are greedy, as well as making it possible to view matches that do not have that strict matching. This allows us to see a wider match result.

[ -.]? This will search for a space, a dash, or a period, and is made optional with the ?.

### Character Escapes
Character escapes allow us to escape the normal way a regex is read to intepret something as a literal piece of a string. { would denote the start of a qualifier, however if a \{ means to search for the actual symbol of { in our search parameters instead of starting the qualifier.

\(?(\d{3})\)

Here we are searching for the ( and the ) literal instead of a grouping.



### Character Classes
Character classes are a regex standard that stands as a set of characters. 

\d{3} the /d will match any alphanumerical number. It's the same as [0-9]

In our code we use it denote a search of 3 digits grouped together instead of a range.

## Author



Link to Github Profile
https://github.com/Godoflaugh

Link to Regex
https://gist.github.com/Godoflaugh/284c8ccfe3875f1e172fcdcedae4fbfc
