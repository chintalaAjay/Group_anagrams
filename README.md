# Group Anagrams - LeetCode

## Problem Statement
Given an array of strings `strs`, group the anagrams together.  
You can return the answer in any order.

An Anagram is a word formed by rearranging the letters of another word using all original characters exactly once.

---

## Example

### Input
```java
strs = ["eat","tea","tan","ate","nat","bat"]
Output
[["bat"],["nat","tan"],["ate","eat","tea"]]
Approach
Idea

If two strings are anagrams, then after sorting their characters they become identical.

Example:

eat → aet
tea → aet
ate → aet

All produce the same sorted string "aet".

We use this sorted string as the key in a HashMap.

Algorithm
Create a HashMap
Key → Sorted String
Value → List of Anagrams
Traverse each string in the array.
Convert string into character array.
Sort the character array.
Convert sorted array back to string.
Use sorted string as key:
If key doesn't exist, create new list.
Add original string to the list.
Return all grouped values from the HashMap.
Java Solution
import java.util.*;

class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {

        HashMap<String, ArrayList<String>> map = new HashMap<>();

        for(String str : strs) {

            char ch[] = str.toCharArray();

            Arrays.sort(ch);

            String key = new String(ch);

            map.putIfAbsent(key, new ArrayList<String>());

            map.get(key).add(str);
        }

        return new ArrayList<>(map.values());
    }
}
Dry Run
Input
["eat","tea","tan","ate","nat","bat"]
Sorted Keys
eat → aet
tea → aet
tan → ant
ate → aet
nat → ant
bat → abt
HashMap
aet → [eat, tea, ate]
ant → [tan, nat]
abt → [bat]
Final Output
[[eat, tea, ate], [tan, nat], [bat]]
Time Complexity

O(n⋅klogk)

Where:

n = Number of strings
k = Maximum length of a string
Space Complexity

O(n⋅k)

Concepts Used
HashMap
Arrays.sort()
Strings
Character Arrays
ArrayList
Anagrams
LeetCode Problem Link

https://leetcode.com/problems/group-anagrams/

Author

Ajay Chintala
