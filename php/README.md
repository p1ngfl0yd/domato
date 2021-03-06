The `php_generated.txt` file was generated by running `parse_types.py` on the
source code of php.

Possible improvements:
- Callbacks are currently unused (`<fuzzfunction>` always point to `phpinfo`).
	Generating callback code in a similar manner to the main function could
	potentially expose additional bugs, especially if callbacks get access to the
	same variables / can mess up stuff that the caller didn't expect.
- Currently, the return values from the function / method calls are ignored.
	In cases where function / method calls return non-trivial types, it be better
	to store these return values in variables and use them as function arguments
	in later calls or potentially call methods on these "generated" objects.
- It would be great to be able to infer the expected classes of the objects
	parameters taken by functions/methods.
- The `parse_type.py` code is ugly, and should be refactored a bit.
- Randomize the references (`$ref_` in template.php).

