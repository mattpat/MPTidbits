MPTidbits, by Matt Patenaude
============================
A set of very small categories for `NSString`, `NSMutableString`, `NSArray`, and 
`NSDictionary` that add a few sorely lacking features (`isEmpty` and `containsKey:` 
methods, for instance).

Documentation
-------------
Most of the methods are relatively self-explanatory, but this should clear things up for those of slightly greater ambiguity.

### Including the Source ###

You can include `MPTidbits` in your project by simply copying all five source files into your project, and then importing the global header file in any file in which you want to use an `MPTidbits` method:

	#import "MPTidbits.h"

### `NSString` Methods ###

These methods can be found in `NSString+MPTidbits.h`.

* `- (BOOL)isEmpty`

	Returns `YES` only if the receiver is either empty (no characters), or contains only whitespace characters.

* `- (BOOL)isEmptyIgnoringWhitespace:(BOOL)ignoreWhitespace`

	If `ignoreWhitespace` is `YES`, returns `YES` only if the receiver is either empty (no characters), or contains only whitespace characters. If `ignoreWhitespace` is `NO`, returns `YES` only if the receiver is empty (no characters) -- it does not ignore whitespace characters.
	
* `- (NSString *)stringByTrimmingWhitespace`

	Returns an `NSString` object identical to the receiver except that any leading or trailing whitespace characters (the characters in the set returned by `NSCharacterSet`'s `+whitespaceCharacterSet`) will be stripped.

* `- (NSString *)MD5Hash`

	Returns an `NSString` object that contains a 32-character hexadecimal representation of the receiver's [MD5 hash](http://en.wikipedia.org/wiki/MD5). This method uses the functions of Foundation's `CommonCrypto` library, which means that your project does **not** have to link against an outside library (eg, OpenSSL).

* `- (NSString *)SHA1Hash`

	Returns an `NSString` object that contains a 40-character hexadecimal representation of the receiver's [SHA-1 hash](http://en.wikipedia.org/wiki/SHA_hash_functions). This method uses the functions of Foundation's `CommonCrypto` library, which means that your project does **not** have to link against an outside library (eg, OpenSSL).

### `NSMutableString` Methods ###

These methods can be found in `NSString+MPTidbits.h`.

* `- (void)trimCharactersInSet:(NSCharacterSet *)aCharacterSet`

	Strips leading and trailing characters from the receiver that belong to `aCharacterSet`. In contrast to `NSString`'s `-stringByTrimmingCharactersInSet:`, this method operates on the receiver in place.

* `- (void)trimWhitespace`

	Strips leading and trailing whitespace characters (the characters in the set returned by `NSCharacterSet`'s `+whitespaceCharacterSet`) from the receiver. In contrast to the above `-stringByTrimmingWhitespace`, this method operates on the receiver in place.

### `NSArray` Methods ###

These methods can be found in `NSCollections+MPTidbits.h`.

* `- (BOOL)isEmpty`

	Returns `YES` only if the receiver contains no objects: the equivalent of `([receiver count] == 0)`.

### `NSDictionary` Methods ###

These methods can be found in `NSCollections+MPTidbits.h`.

* `- (BOOL)isEmpty`

	Returns `YES` only if the receiver contains no objects: the equivalent of `([receiver count] == 0)`.

* `- (BOOL)containsKey:(NSString *)aKey`

	Returns `YES` only if the key `aKey` has an associated object in the receiver.

* `- (BOOL)containsKey:(NSString *)aKey allowEmptyValue:(BOOL)allowEmpty`

	If `allowEmpty` is `YES`, returns `YES` only if the key `aKey` has an associated object in the receiver. If `allowEmpty` is `NO`, returns `YES` only if the key `aKey` has an associated object in the receiver, and that object is neither the `NSNull` object, nor does it return `YES` to an `isEmpty` message (if the object responds to it). This method is useful if you want to quickly check if a key both exists, and is not an empty string, for example.

License
-------
`MPTidbits` is licensed under the MIT license, excerpted below.

	Copyright 2008 - 2009 Matt Patenaude. All rights reserved.

	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:

	The above copyright notice and this permission notice shall be included in
	all copies or substantial portions of the Software.

	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
	THE SOFTWARE.