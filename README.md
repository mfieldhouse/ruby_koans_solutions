# Ruby Koans Solutions

Ruby Koans available from http://rubykoans.com/ and their solutions.

## Study Notes

### about_array_assignment

**The splat Operator**

When an lvalue is preceded by an asterisk, all remaining rvalues are placed in an array and assigned to that lvalue

`a, *b = 1, 2, 3`  
`a #=> 1`   
`b #=> [2, 3]`

When there are too few rvalues to assign to lvalues, the variable is assigned nil

### about_hashes

**Hash Default Values**

Hashes have a default value that is returned when accessing keys which do not exist. By default this is nil.

**Q: Why would you want to use #fetch instead of #[] when accessing hash keys?**  
A: #fetch raises an exception KeyError if the key does not exist. #[] returns nil.
   Use fetch if you are not sure the key exists and want to return an error if it does not.

`hash = Hash.new('test')`
Sets the default return value to the string 'test'

`hash[:one] = "dog"`  
`hash[:one] #=> "dog"`  
`hash[:two] #=> "test"`

### about_strings

**Q: Ruby programmers tend to favor the shovel operator (<<) over the # plus equals operator (+=) when building up strings.  Why?**  
A: << modifies the string in place, whereas += creates a new one. Further explanation here http://library.edgecase.com/a-little-more-about-strings

`1.9.3-p194 :001 > a = "foo"`  
` => "foo"`  
`1.9.3-p194 :002 > a.object_id`  
` => 70283949004920`  
`1.9.3-p194 :003 > a << " bar"`  
` => "foo bar"`  
`1.9.3-p194 :004 > a.object_id`  
` => 70283949004920`  
`1.9.3-p194 :005 > a += " baz"`  
` => "foo bar baz"`  
`1.9.3-p194 :006 > a.object_id`  
` => 70283948969420`  

**Strings can be split using regular expressions**

`a = "the:rain:in:spain"`  
`a.split(/:/)`  
`#=>  ["the", "rain", "in", "spain"]`