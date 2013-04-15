# Ruby Koans Solutions

Ruby Koans available from http://rubykoans.com/ and their solutions.

## Study Notes

### about_array_assignment

**The splat Operator**

When an lvalue is preceded by an asterisk, all remaining rvalues are placed in an array and assigned to that lvalue

`a, *b = 1, 2, 3`  
`a => 1`   
`b => [2, 3]`

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
`hash[:one] => "dog"`  
`hash[:two] => "test"`

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
`=>  ["the", "rain", "in", "spain"]`

### about_symbols

to_s is called on interpolated symbols.

Symbols stay in memory until the program exits.

### about_regular_expressions

A failed match returns nil.

Regular expression operators are greedy. As many occurences as possible are matched while still allowing the 
overall match to succeed. A greedy metacharacter can be made lazy by following it with a ?

The left most match wins  
`"abbcc az[/az*/]"`  
`=> "a"`

`#select` invokes the block for each element and returns an array of the original elements for which the block returns true

`["cat", "bat", "rat", "zat"].select { |a| a[/[cbr]at/] }`  
`=> ["cat", "bat", "rat"]`

`\w` - Any word character. a-z, A-Z, 0-9 or underscore. No spaces allowed.  
`.` - period is any non newline character.

Capital negates. `\W` - not a word character. `\D` - not a digit.

A regular expression can be assigned to a variable.

`grays = /(James|Dana|Summer) Gray/`  
`"James Gray"[grays]`
`=> "James Gray"`

**scan = find all**  
**sub = find and replace**  
**gsub = find and replace all**  

### about_methods

`eval` takes a string and executes it as code  
`eval("Time.now")`

The context which code is executed in is called a binding.

The last thing to be evaluated in a method is returned.

When return is used in a method, only the object it specifies is returned, even if it is not the last.

`def method_with_explicit_return  
  :a_non_return_value  
  return :return_value  
  :another_non_return_value  
end`  
`=> :return_value`

A variable args method returns an array and is of class Array.

Inside a class def creates a new instance method.  
When self is used inside a class, a new class method is created.

**Private and Protected Methods**

Calling private methods with an explicit receiver raises NoMethodError.  
This includes using self from within other methods of the class and when trying to use the method on an instance of the class

### about_constants

Top level constants are referenced by double colons

