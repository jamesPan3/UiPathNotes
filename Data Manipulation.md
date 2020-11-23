# Data Manipulation
The process of modifying, structuring, formatting, or sorting through data in order to facilitate its usage and increase its management capabilities.

## Strings
**String Methods**
- **Concat** Concatenates the string representations of two specified objects. 
    - Expression: String.Concat (VarName1, VarName2)
- **Contains** Checks whether a specified substring occurs within a string. Returns true or false.
    - Expression: VarName.Contains (“text”)
- **Format** Converts the value of objects to strings (and inserts them into another text). 
    - Expression: String.Format(“{0} is {1}”, VarName1, VarName2)
- **IndexOf** Returns the zero-based index of the first occurrence of a character in a String. 
    - Expression: VarName1.IndexOf(“a”)
- **Join** Concatenates the elements in a collection and displays them as String. 
    - Expression: String.Join(“|”, CollVarName1)
- **Replace** Replaces all the occurrences of a substring in a string. 
    - Expression: VarName.Replace (“original”, “replaced”)
- **Split** Splits a string into substrings using a given separator. 
    - Expression: VarName.Split(“|“c)(index)
- **Substring** Extracts a substring from a string using the starting index and the length. 
    - Expression: VarName1.Substring(startIndex, length)