# Why are the "Author" & "SubDesc" variables not displaying at all on the page?

What is Portable Text? 
represents a JSON based rich text specification for modern content editing platforms. Portable Text is designed to be a format for text editing interfaces and for serializing into any human-readable format. 

## Are we able to display the category variable? 
NO
### Objective: 
To be certain that the problem represents a consideration of the variable (type array) and that the problem does not emerge from elsewhere.

### Result/Answer: 
It is necessary to specify the type component of category. This means that the Array type is not recognised as an extraction property. The aim now is to discover how to access datas inside variable array type with portableText and Sanity library in REACT.

## Identify the problem: 
In the default RichText export component, the parameter has been named "props" with a default object type value assigned to "any". Initially set up on BlockContent. 

In RichText retrieval, variables cannot be retrieved because they are considered to be arrays. 

Why does the following error appear: "[@portabletext/react] Unknown block type "undefined", specify a component for it in the `components.types` prop"?
I'll clarify my question as follows: at what file level/scale does this error occur?

Is it when establishing typing in the schemaTypes folder?

Is it when attempting to fetch data when using portableTextComponents? 

FINAL QUESTION: How can I access a variable located in an array using portableTextComponent? We'd be delighted to give you an example.



## ALTERNATIVE SOLUTIONS: 

1) A Block Type has not been defined in portable text

2) A new variable type has been baddly declared/exported in Sanity's project
When is portableTextBlock used? 