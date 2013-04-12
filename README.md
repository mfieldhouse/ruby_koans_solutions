# Ruby Koans Solutions

Ruby Koans available from http://rubykoans.com/ and their solutions.

## Study Notes

### about_array_assignment

When an lvalue is preceded by an asterisk, all remaining rvalues are placed in an array and assigned to that lvalue

a, *b = 1, 2, 3
a == 1
b == [2, 3]

When there are too few rvalues to assign to lvalues, the variable is assigned nil

### about_hashes

Q: Why would you want to use #fetch instead of #[] when accessing hash keys?
A: #fetch raises an exception KeyError if the key does not exist. #[] returns nil.
   Use fetch if you are not sure the key exists and want to return an error if it does not.

Hashes return the default value of nil when a key does not exist.

hash = Hash.new('test')
Sets the default return value to the string 'test'