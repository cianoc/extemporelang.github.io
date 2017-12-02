# Introduction

The core functions and variables that load at launch.

# Memory
## size_t
Type: AliasAlias: i64
Value: Pointer Size (on 32 bit systems it is 32, on 64 bit it will be 64 bit)

This should only be necessary if you're calling foreign functions.

## size_of_type
Type: Macro

### Parameters
1. type : type name

### Returns
+ i64 : bytesize of this type.

### Description
Extempore's version of size_of (C/C++ function). How much memory is taken up by a particular type. For tuples, and other types built upon memory references, the size takes into account pointer sizes, and not the size of memory pointed to.

### Example
``($ (size_of i64))``

## inc
Type: Macro

### Parameters
1. ``x`` : Variable to be incremented. This must be a type that supports basic math functions.
2. ``y`` : Amount to increment ``x``. This must the same type as ``x``.

### Returns
+ Returns the result. The return value will be the same type as ``x``.

### Description
Increments x by y.

### Example
TODO

## dec
Type: Macro

### Parameters
1. ``x`` : Variable to be decremented. This must be a type that supports basic math functions.
2. ``y`` : Amount to decrement ``x``. This must the same type as ``x``.

### Returns
+ Returns the result. The return value will be the same type as ``x``.

### Description
Decrements x by y.

### Example
TODO

## min
Type: Macro

### Parameters
1. ``x`` : Variable to be compared. This must be a type that supports less than/equal.
2. ``y`` : Variable to be compared. This must the same type as ``x``.

### Returns
+ Returns the smallest value. The return value will be the same type as ``x``.

### Description
Minimum of ``x`` and ``y``.

### Example
TODO

## max
Type: Macro

### Parameters
1. ``x`` : Variable to be compared. This must be a type that supports less than/equal.
2. ``y`` : Variable to be compared. This must the same type as ``x``.

### Returns
+ Returns the largest value. The return value will be the same type as ``x``.

### Description
Returns the largest of the two values.

### Example
TODO

## clamp
Type: Macro

### Parameters
1. ``x`` : Input value. Must be a type that supports <>=.
2. ``minval`` : Minimum value in range. Must be same type as ``x``.
3. ``maxval`` : Maximum value in range. Must be same type as ``x``.

### Returns
+ The return value is the same type as ``x``.

### Description
Clamp input value to range. If ``x < minval`` it will return minval, if ``y > maxval`` it will return maxval. Otherwise it returns x. 

### Example
TODO

## log
Type: Closure
### Types
+ log:[float,float]
+ log:[double,double]

### Description
returns the natural logarithm (ln)

## logn
Type: Macro

### Types
+ ``float``
+ ``double``

### Parameters
1. ``x`` : x value
2. ``base`` : base of the logarithm

### Description
Returns log of x with base ``base``

### Example
``($ (log 100, 10)) ;; log10 of 100 (returns 2)``

## deg2rad
Type: Macro

### Supported Types
+ ``float``
+ ``double``

### Parameters
1. ``degrees`` : x value in degrees

### Returns
+ Same type as ``degrees``

### Description
Converts a value in degrees to radians. 

### Example
TODO

## rad2deg
Type: Macro

### Supported Types
+ ``float``
+ ``double``

### Parameters
1. ``radians`` : x value in radians

### Returns
+ Same type as ``radians``

### Description
Converts a value in radians to degrees.

### Example
TODO

## evenp
Type: Macro
### Supported Types
+ i8
+ i16
+ i32

### Parameters
1. x - the value that you are testing. Must be an integer of some kind.

### Return Value Type
+ ``i1`` : 1 if ``x`` is even, 0 otherwise

### Description
Checks to see if a value is even. Returns a C boolean (i1).


## oddp
Type: Macro
### Supported Types
+ i8
+ i16
+ i32

### Parameters
1. x - the value that you are testing. Must be an integer of some kind.

### Return Value Type
+ ``i1`` : 1 if ``x`` is odd, 0 otherwise

### Description
Checks to see if a value is even. Returns a C boolean (i1).


# Math Constants

## NaNf
Constant
Type: float
Value: Single precision not-a-number

## NaN
Constant
Type: double
Value: Double precision not a number

## nan32
Constant
Type: i32
Value: Integer not a number TODO

## nan64
Constant
Type: i64
Value: Integer not a number TODO

## n32
Constant
Type: i32*
Value: TODO Integer not a number TODO

## n64
Constant
Type: i64*
Value: TODO Integer not a number TODO



## PIf
Constant
Type: float
Value: pi (3.14159...)

## TWOPIf
Constant
Type: float
Value: 2 * pi (6.2831...)

## Ef

Constant
Type: float
Value: e (base of natural log)

## PI

Constant
Type: double
Value: pi (3.14159...)

## TWOPI

Constant
Type: double
Value: 2 * pi (6.2831...)

## E

Constant
Type: double
Value: e (base of natural log)

# Math Functions

## random
Type: Polymorphic Closure

### Types
+ [float]* 
+ [double]* 
+ [i32,i32]*
+ [i64,i64]*
+ [float,float]*
+ [double,double]*
+ [i32,i32,i32]*
+ [i64,i64,i64]*
+ [float,float,float]*
+ [double,double,double]*

### Description
If called with 0 arguments it will return a pseudo random value between 0.0 and 1.0

If called with 1 argument, ``arg1`` it will return a pseudo random value ``x`` where 0 <= x < arg1.

If called with 2 arguments, ``arg1`` and ``arg2`` it will return pseudo random values ``x``  where arg1 <= x < arg2.

## tan
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameters
1. ``x`` : Angle in radians.

### Description
Returns tan(x)

## atan
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameters
1. ``x``

### Returns
+ Angle of x in radians.

### Description
Inverse tangent. Returns atan(x)

## tanh
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameter
1. ``x`` : Angle in radians

### Description
Hyperbolic tangent. It returns tanh(x)

## sin
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameters
1. ``x`` : Angle in radians.

### Description
Returns sin(x)

## asin
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameters
1. ``x``

### Returns
+ Angle of x in radians.

### Description
Inverse sine. Returns atan(x)

## sinh
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameter
1. ``x`` : Angle in radians

### Description
Hyperbolic sine. It returns sinh(x)

## cos
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameters
1. ``x`` : Angle in radians.

### Description
Returns cosine(x)

## acos
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameters
1. ``x``

### Returns
+ Angle of x in radians.

### Description
Inverse cosine. Returns acos(x)

## cosh
Type: Polymorphic Closure

### Types
+ [float,float]* 
+ [double,double]* 

### Parameter
1. ``x`` : Angle in radians

### Description
Hyperbolic cosine. It returns cosh(x)



# Audio Constants and Types

## SAMPLE

Type Alias
Type: float
Value Audio I/O sample type in the dsp processing chain

## DSP
__Type Alias__ : [SAMPLE,SAMPLE,i64,i64,SAMPLE]

### Parameters
1. __in:SAMPLE__ : input sample from sound card
2. __chan:i64__ : the channel that the current sample comes from, and the corresponding channel that the current sample will go to.
3. __TODO:i64__ : TODO what is this?
4. __data:SAMPLE__ : TODO currently unused.

### Returns
+ __SAMPLE__ : output sample. This will be sent to chan

### Description
Audio call back function that is single sample and single threaded.

### Example
TODO

## DSPMT
__Type Alias__ : [SAMPLE,SAMPLE*,i64,i64,SAMPLE]

### Parameters
1. __in:SAMPLE*__ : TODO Is this correct? input sample from sound card. Think it's actually multiple inputs.
2. __chan:i64__ : the channel that the current sample comes from, and the corresponding channel that the current sample will go to.
3. __TODO:i64__ : TODO what is this?
4. __data:SAMPLE__ : TODO currently unused.

### Returns
+ __SAMPLE__ : output sample. This will be sent to channel 'chan'

### Description
Audio call back function that is single sample and multi threaded.

### Example
TODO

## DSPMC
__Type Alias__ : [void,SAMPLE*,SAMPLE*,i64,i8* ]

### Parameters
1. __in:SAMPLE__ : input sample block from sound card for all channels. This holds all input channels in an interleaved buffer.
2. __out:SAMPLE__ : pointer to output sample block to write audio. This holds all output channels in an interleaved buffer.
3. __chan:i64__ : the channel that the current sample comes from, and the corresponding channel that the current sample will go to.
4. __TODO:i64__ : TODO what is this? time?
5. __data:i8*__ : TODO currently unused.

### Description
Audio call back function that process audio blocks of size ``FRAME``.

### Example
TODO

## DSPMCMT
__Type Alias__ : [void, SAMPLE** ,SAMPLE*,i64,i8* ]

### Parameters
1. __in:SAMPLE**_ : TODO input sample block from sound card for all channels. This holds all input channels in an interleaved buffer.
2. __out:SAMPLE*__ : pointer to output sample block to write audio. This holds all output channels in an interleaved buffer.
3. __chan:i64__ : the channel that the current sample comes from, and the corresponding channel that the current sample will go to.
4. __TODO:i64__ : TODO what is this? time?
5. __data:i8*__ : TODO currently unused.

### Description
Multi-threaded audio call back function that process audio blocks of size ``NUM_FRAMES``.

### Example
TODO

## SPI
Constant
Type: SAMPLE
Value: PI (3.1415...)

## STWOPI
Constant
Type: SAMPLE
Value: 2 * PI (6.2831...)

## SE
Constant
Type: SAMPLE
Value: e (base of natural log)

## SAMPLE_RATE
Constant
Type: i32
Value: Audio sound card sample rate

## SAMPLERATE
Constant
Type: SAMPLE
Value: Audio sound card sample rate

## SRs
Constant
Type: SAMPLE
Value: Audio sound card sample rate.

## SRf
Constant
Type: float
Value: Audio sound card sample rate

## SRd
Constant
Type: double
Value: Audio sound card sample rate

## SR
Constant
Type: i64
Value: Audio sound card sample rate

## CHANNELS
Constant
Type: i32
Value: Number of audio output channels on sound card.

## IN_CHANNELS
Constant
Type: i32
Value: Number of audio input channels on sound card.

## NUM_FRAMES
Constant
Type: i32
Value: Audio signal block size

## FRAMES
Constant
Type: i64
Value: Audio signal block size

# I/O

## print_return
``print_return::[void]*``

### Description
Prints a line return to the output buffer (e.g. where extempore is running).

## print_space
``print_space::[void]*``

### Description
Prints a space to the output buffer (e.g. where extempore is running).

## print
``print``
type: overloaded

### Types
+ [void,i1]*
+ [void,i8]*
+ [void,i16]*
+ [void,i32]*
+ [void,i64]*
+ [void,float]*
+ [void,double]*
+ [void,!a]*
+ [void,mzone*]*
+ [void,Symbol*]*

### Description
Prints the value to the console.

For generic types, the generic type must be one of the following:
+ An array containing a type that can be printed
+ A pointer to a type that can be printed
+ A tuple of length 1->6 containing types that can be printed.
+ A user defined type that provides a ``print`` function.
+ A memory zone
+ A symbol (empty symbols will print a zero length symbol)

Overloads and should be used via the `println` function
If the symbol is empty will print a zero length symbol

### Description
Prints a line return to the output buffer (e.g. where extempore is running).

# Memory
## Zone
TODO Type?

### Parameters
1. ``size:i64`` : Size in bytes TODO Is this correct?

### Returns
+ TODO? 

### Description
TODO

## push_zone
TODO Need a type

### Parameters
1. TODO

### Returns
+ TODO? 

### Description
TODO

## pop_zone
TODO Need a type

### Parameters
1. TODO

### Returns
+ TODO? 

### Description
TODO

## reset_zone
TODO Need a type

### Parameters
1. TODO

### Returns
+ TODO? 

### Description
TODO What does this do?

## destroy_zone
TODO Need a type

### Parameters
1. TODO

### Returns
+ TODO? 

### Description
Frees the memory in the zone.

## peek_zone
TODO Need a type

### Parameters
1. TODO

### Returns
+ TODO? 

### Description
TODO

## zcopy
Type: Polymorphic Closure

### Parameters
1. ``x`` : size of memory area to be copied (the units are the size of the type. e.g. if the memzones are in i64s, and x is 4, then it will be 4 * sizeof(i64)
2. ``fromz`` : a pointer to the zone to be copied
3. ``toz`` : a pointer to the destination memory zone

### Types
This function should support all built in types and user defined types.

### Description
A function to copy data from one memory zone to another.

# Control Flow
## ->
Type: Macro

### Description
A 'thread-first' macro.

This macro can help make code more readable by removing nesting.
Threads the first expr passed to the macro into the first position in
the second sexp. Recursively continues to thread the resultant sexp
into any further sexp arguments."

### Examples
TODO - Quite badly needed really...

## ->>
Type: Macro

### Description
A 'thread-last' macro.

This macro can help make code more readable by removing nesting.
Threads the first expr passed to the macro into the last position in
the second sexp. Recursively continues to thread the resultant sexp
into any further sexp arguments."

### Examples
TODO - Quite badly needed really...

# Interop

## get_native_name
type: scheme macro

## Parameters
1. ``closure-name`` : Extempore closure name

## Returns
+ A string that can be used in Scheme to call this closure.

## Description
See Extempore-Scheme interop description in the tutorial.

## get_native_fptr
type: macro

### Parameters
1. ``closure-name`` : Extempore closure name

### Returns
+ A a pointer to the function that can be used by other languages (e.g. C) for callbacks, etc.

### Description
See FFI description in the tutorial.




# Native Functions
These are C functions that you can call directly from extempore:
    ("abort" . #((213 -1) "" ())) ;; libc
    ("abs" . #((213 4 4) "" ())) ;; libc
    ("ascii_text_color" . #((213 -1 4 4 4) "" ())) ;; xtlang
    ("asin" . #((213 0 0) "" ())) ;; libm
    ("atof" . #((213 0 108) "" ())) ;; libc
    ("atoi" . #((213 4 108) "" ())) ;; libc
    ("atol" . #((213 2 108) "" ())) ;; libc
    ("audio_clock_base" . #((213 0) "" ())) ;; xtlang
    ("audio_clock_now" . #((213 0) "" ())) ;; xtlang
    ("base64_decode" . #((213 108 108 2 2) "" ())) ;; xtlang
    ("base64_encode" . #((213 108 108 2 2) "" ())) ;; xtlang
    ("calloc" . #((213 108 2 2) "" ())) ;; libc
    ("cbrt" . #((213 0 0) "" ())) ;; libm
    ("cbrtf" . #((213 1 1) "" ())) ;; libm
    ("clearerr" . #((213 -1 108) "" ())) ;; libc
    ("clock_clock" . #((213 0) "" ())) ;; xtlang
    ("cname_decode" . #((213 108 108 2 2) "" ())) ;; xtlang
    ("cname_encode" . #((213 108 108 2 2) "" ())) ;; xtlang
    ("copysign" . #((213 0 0 0) "" ())) ;; libm
    ("copysignf" . #((213 1 1 1) "" ())) ;; libm
    ("cosh" . #((213 0 0) "" ())) ;; libm
    ("coshf" . #((213 1 1) "" ())) ;; libm
    ("ctermid" . #((213 108 108) "" ())) ;; libc
    ("dlsym" . #((213 108 108 108) "" ())) ;; libdl (!WIN32) - could be implemented on WIN32 - just used for OpenGL(?)
    ("dtof" . #((213 1 0) "" ())) ;; xtlang
    ("dtoi1" . #((213 10 0) "" ())) ;; xtlang
    ("dtoi16" . #((213 6 0) "" ())) ;; xtlang
    ("dtoi32" . #((213 4 0) "" ())) ;; xtlang
    ("dtoi64" . #((213 2 0) "" ())) ;; xtlang
    ("dtoi8" . #((213 8 0) "" ())) ;; xtlang
    ("dtoui1" . #((213 10 0) "" ())) ;; xtlang
    ("dtoui16" . #((213 6 0) "" ())) ;; xtlang
    ("dtoui32" . #((213 4 0) "" ())) ;; xtlang
    ("dtoui64" . #((213 2 0) "" ())) ;; xtlang
    ("dtoui8" . #((213 8 0) "" ())) ;; xtlang
    ("erf" . #((213 0 0) "" ())) ;; libm
    ("erfc" . #((213 0 0) "" ())) ;; libm
    ("erfcf" . #((213 1 1) "" ())) ;; libm
    ("erff" . #((213 1 1) "" ())) ;; libm
    ("exit" . #((213 -1 4) "" ())) ;; libc
    ("expm1" . #((213 0 0) "" ())) ;; libm
    ("expm1f" . #((213 1 1) "" ())) ;; libm
    ("extitoa" . #((213 108 2) "" ())) ;; xtlang (for kinect only?)
    ("fclose" . #((213 4 108) "" ())) ;; libc
    ("fdim" . #((213 0 0 0) "" ())) ;; libm
    ("fdimf" . #((213 1 1 1) "" ())) ;; libm
    ("fdopen" . #((213 108 4 108) "" ())) ;; libc
    ("feof" . #((213 4 108) "" ())) ;; libc
    ("ferror" . #((213 4 108) "" ())) ;; libc
    ("fflush" . #((213 4 108) "" ())) ;; libc
    ("fgetc" . #((213 4 108) "" ())) ;; libc
    ("fgets" . #((213 108 108 4 108) "" ())) ;; libc
    ("fileno" . #((213 4 108) "" ())) ;; libc
    ("flockfile" . #((213 -1 108) "" ())) ;; libpthread
    ("fmax" . #((213 0 0 0) "" ())) ;; libm
    ("fmaxf" . #((213 1 1 1) "" ())) ;; libm
    ("fmin" . #((213 0 0 0) "" ())) ;; libm
    ("fminf" . #((213 1 1 1) "" ())) ;; libm
    ("fmod" . #((213 0 0 0) "" ())) ;; libm
    ("fmodf" . #((213 1 1 1) "" ())) ;; libm
    ("fopen" . #((213 108 108 108) "" ())) ;; libc
    ("fputc" . #((213 4 4 108) "" ())) ;; libc
    ("fputs" . #((213 4 108 108) "" ())) ;; libc
    ("fread" . #((213 2 108 2 2 108) "" ())) ;; libc
    ("free" . #((213 -1 108) "" ())) ;; libc (via xtlang)
    ("free16" . #((213 -1 108) "" ())) ;; xtlang
    ("free_after_delay" . #((213 -1 108 0) "" ())) ;; xtlang
    ("freopen" . #((213 108 108 108 108) "" ())) ;; libc
    ("fseek" . #((213 4 108 2 4) "" ())) ;; libc
    ("ftell" . #((213 2 108) "" ())) ;; libc
    ("ftod" . #((213 0 1) "" ())) ;; xtlang
    ("ftoi1" . #((213 10 1) "" ())) ;; xtlang
    ("ftoi16" . #((213 6 1) "" ())) ;; xtlang
    ("ftoi32" . #((213 4 1) "" ())) ;; xtlang
    ("ftoi64" . #((213 2 1) "" ())) ;; xtlang
    ("ftoi8" . #((213 8 1) "" ())) ;; xtlang
    ("ftoui1" . #((213 10 1) "" ())) ;; xtlang
    ("ftoui16" . #((213 6 1) "" ())) ;; xtlang
    ("ftoui32" . #((213 4 1) "" ())) ;; xtlang
    ("ftoui64" . #((213 2 1) "" ())) ;; xtlang
    ("ftoui8" . #((213 8 1) "" ())) ;; xtlang
    ("fp80ptrtod" . #((213 0 108) "" ())) ;; xtlang
    ("ftrylockfile" . #((213 4 108) "" ())) ;; libpthread
    ("funlockfile" . #((213 -1 108) "" ())) ;; libpthread
    ("fwrite" . #((213 2 108 2 2 108) "" ())) ;; libc
    ("getc" . #((213 4 108) "" ())) ;; libc
    ("getc_unlocked" . #((213 4 108) "" ())) ;; libc
    ("getchar" . #((213 4) "" ())) ;; libc
    ("getchar_unlocked" . #((213 4) "" ())) ;; libc
    ("getenv" . #((213 108 108) "" ())) ;; libc
    ("gets" . #((213 108 108) "" ())) ;; libc
    ("getw" . #((213 4 108) "" ())) ;; libc
    ("hypot" . #((213 0 0 0) "" ())) ;; libm
    ("hypotf" . #((213 1 1 1) "" ())) ;; libm
    ("i16tod" . #((213 0 6) "" ())) ;; xtlang
    ("i16tof" . #((213 1 6) "" ())) ;; xtlang
    ("i16toi1" . #((213 10 6) "" ())) ;; xtlang
    ("i16toi32" . #((213 4 6) "" ())) ;; xtlang
    ("i16toi64" . #((213 2 6) "" ())) ;; xtlang
    ("i16toi8" . #((213 8 6) "" ())) ;; xtlang
    ("i16toptr" . #((213 108 6) "" ())) ;; xtlang
    ("i16toui32" . #((213 4 6) "" ())) ;; xtlang
    ("i16toui64" . #((213 2 6) "" ())) ;; xtlang
    ("i1tod" . #((213 0 10) "" ())) ;; xtlang
    ("i1tof" . #((213 1 10) "" ())) ;; xtlang
    ("i1toi16" . #((213 6 10) "" ())) ;; xtlang
    ("i1toi32" . #((213 4 10) "" ())) ;; xtlang
    ("i1toi64" . #((213 2 10) "" ())) ;; xtlang
    ("i1toi8" . #((213 8 10) "" ())) ;; xtlang
    ("i32tod" . #((213 0 4) "" ())) ;; xtlang
    ("i32tof" . #((213 1 4) "" ())) ;; xtlang
    ("i32toi1" . #((213 10 4) "" ())) ;; xtlang
    ("i32toi16" . #((213 6 4) "" ())) ;; xtlang
    ("i32toi64" . #((213 2 4) "" ())) ;; xtlang
    ("i32toi8" . #((213 8 4) "" ())) ;; xtlang
    ("i32toptr" . #((213 108 4) "" ())) ;; xtlang
    ("i32toui64" . #((213 2 4) "" ())) ;; xtlang
    ("i64tod" . #((213 0 2) "" ())) ;; xtlang
    ("i64tof" . #((213 1 2) "" ())) ;; xtlang
    ("i64toi1" . #((213 10 2) "" ())) ;; xtlang
    ("i64toi16" . #((213 6 2) "" ())) ;; xtlang
    ("i64toi32" . #((213 4 2) "" ())) ;; xtlang
    ("i64toi8" . #((213 8 2) "" ())) ;; xtlang
    ("i64toptr" . #((213 108 2) "" ())) ;; xtlang
    ("i8tod" . #((213 0 8) "" ())) ;; xtlang
    ("i8tof" . #((213 1 8) "" ())) ;; xtlang
    ("i8toi1" . #((213 10 8) "" ())) ;; xtlang
    ("i8toi16" . #((213 6 8) "" ())) ;; xtlang
    ("i8toi32" . #((213 4 8) "" ())) ;; xtlang
    ("i8toi64" . #((213 2 8) "" ())) ;; xtlang
    ("i8toui32" . #((213 4 8) "" ())) ;; xtlang
    ("i8toui64" . #((213 2 8) "" ())) ;; xtlang
    ("ilogb" . #((213 0 0) "" ())) ;; libm
    ("ilogbf" . #((213 1 1) "" ())) ;; libm
    ("imp_rand1_d" . #((213 0 0) "" ())) ;; xtlang
    ("imp_rand1_f" . #((213 1 1) "" ())) ;; xtlang
    ("imp_rand1_i32" . #((213 4 4) "" ())) ;; xtlang
    ("imp_rand1_i64" . #((213 2 2) "" ())) ;; xtlang
    ("imp_rand2_d" . #((213 0 0 0) "" ())) ;; xtlang
    ("imp_rand2_f" . #((213 1 1 1) "" ())) ;; xtlang
    ("imp_rand2_i32" . #((213 4 4 4) "" ())) ;; xtlang
    ("imp_rand2_i64" . #((213 2 2 2) "" ())) ;; xtlang
    ("imp_randd" . #((213 0) "" ())) ;; xtlang
    ("imp_randf" . #((213 1) "" ())) ;; xtlang
    ("impc_false" . #((113 10) "" ())) ;; internal
    ("impc_null" . #((113 108) "" ())) ;; internal
    ("impc_true" . #((113 10) "" ())) ;; internal
    ("lgamma" . #((213 0 0) "" ())) ;; libm
    ("lgammaf" . #((213 1 1) "" ())) ;; libm
    ("llabs" . #((213 2 2) "" ()))
    ("llrint" . #((213 2 0) "" ()))
    ("llrintf" . #((213 2 1) "" ()))
    ("llround" . #((213 2 0) "" ()))
    ("llroundf" . #((213 2 1) "" ()))
    ("llvm_destroy_zone_after_delay" . #((213 -1 "%mzone*" 2) "" ())) ;; internal but referenced in tests
    ("fprintf" . #(varargs "" ())) ;; libc
    ("fscanf" . #(varargs "" ())) ;; libc
    ("llvm_get_function_ptr" . #((213 108 108) "" ())) ;; xtlang
    ("llvm_now" . #((213 2) "" ())) ;; xtlang (as now)
    ("llvm_peek_zone_stack" . #((213 "%mzone*") "" ())) ;; xtlang
    ("llvm_pop_zone_stack" . #((213 "%mzone*") "" ()));; xtlang
    ("llvm_print_f32" . #((213 -1 1) "" ())) ;; debug
    ("llvm_print_f64" . #((213 -1 0) "" ())) ;; debug
    ("llvm_print_i32" . #((213 -1 4) "" ())) ;; debug
    ("llvm_print_i64" . #((213 -1 2) "" ())) ;; debug
    ("llvm_print_pointer" . #((213 -1 108) "" ())) ;; debug
    ("llvm_ptr_in_current_zone" . #((213 10 108) "" ())) ;; debug (?)
    ("llvm_ptr_in_zone" . #((213 10 "%mzone*" 108) "" ())) ;; xtlang
    ("llvm_runtime_error" . #((213 -1 2 108) "" ())) ;; debug (?)
    ("llvm_send_udp" . #((213 -1 108 4 108 4) "" ())) ;; xtlang
    ("llvm_zone_copy_ptr" . #((213 10 108 108) "" ())) ;; ???
    ("llvm_zone_create" . #((213 "%mzone*" 2) "" ())) ;; internal (used for Zone)
    ("llvm_zone_destroy" . #((213 -1 "%mzone*") "" ())) ;; internal (for destroy_zone)
    ("llvm_zone_malloc" . #((213 108 "%mzone*" 2) "" ())) ;; xtlang
    ("llvm_zone_malloc_from_current_zone" . #((213 108 2) "" ())) ;; internal (?)
    ("llvm_zone_print" . #((213 -1 "%mzone*") "" ())) ;; internal (for print)
    ("llvm_zone_ptr_size" . #((213 2 108) "" ())) ;; internal (for zcopy)
    ("llvm_zone_reset" . #((213 "%mzone*" "%mzone*") "" ())) ;; internal (for reset_zone)
    ("llvm_disassemble" . #((213 i8* i8* i32) "" ())) ;; xtlang
    ("log1p" . #((213 0 0) "" ())) ;; libm
    ("log1pf" . #((213 1 1) "" ())) ;; libm
    ("log2f" . #((213 1 1) "" ())) ;; libm
    ("logb" . #((213 4 0) "" ())) ;; libm
    ("logbf" . #((213 4 1) "" ())) ;; libm
    ("longjmp" . #((213 -1 108 4) "" ())) ;;libc
    ("lrint" . #((213 2 0) "" ())) ;; libm
    ("lrintf" . #((213 2 1) "" ())) ;; libm
    ("lround" . #((213 4 0) "" ())) ;; libm
    ("lroundf" . #((213 4 1) "" ())) ;; libm
    ("malloc" . #((213 108 2) "" ())) ;; libc (via xtlang)
    ("malloc16" . #((213 108 2) "" ())) ;; xtlang
    ("memccpy" . #((213 108 108 108 4 2) "" ()))
    ("memchr" . #((213 108 108 4 2) "" ()))
    ("memcmp" . #((213 4 108 108 2) "" ()))
    ("memcpy" . #((213 -1 108 108 2) "" ()))
    ("memmove" . #((213 108 108 108 2) "" ()))
    ("memset" . #((213 108 108 4 2) "" ()))
    ("mk_cptr" . #((213 108 108 108) "" ()))
    ("mk_double" . #((213 108 108 0) "" ()))
    ("mk_float" . #((213 108 108 1) "" ()))
    ("mk_i1" . #((213 108 108 10) "" ()))
    ("mk_i16" . #((213 108 108 6) "" ()))
    ("mk_i32" . #((213 108 108 4) "" ()))
    ("mk_i64" . #((213 108 108 2) "" ()))
    ("mk_i8" . #((213 108 108 8) "" ()))
    ("mk_string" . #((213 108 108 108) "" ()))
    ("mutex_create" . #((213 108) "" ()))
    ("mutex_destroy" . #((213 4 108) "" ()))
    ("mutex_lock" . #((213 4 108) "" ()))
    ("mutex_trylock" . #((213 4 108) "" ()))
    ("mutex_unlock" . #((213 4 108) "" ()))
    ("nan" . #((213 0 108) "" ()))
    ("nanf" . #((213 1 108) "" ()))
    ("new_address_table" . #((213 "%clsvar*") "" ()))
    ("next_prime" . #((213 2 2) "" ()))
    ("nextafter" . #((213 0 0 0) "" ()))
    ("nextafterf" . #((213 1 1 1) "" ()))
    ("nexttoward" . #((213 0 0 0) "" ()))
    ("nexttowardf" . #((213 1 1 1) "" ()))
    ("pclose" . #((213 4 108) "" ()))
    ("perror" . #((213 -1 108) "" ()))
    ("popen" . #((213 108 108 108) "" ()))
    ("printf" . #(varargs "" ())) ;; libc
    ("ptrtoi16" . #((213 6 108) "" ()))
    ("ptrtoi32" . #((213 4 108) "" ()))
    ("ptrtoi64" . #((213 2 108) "" ()))
    ("putc" . #((213 4 4 108) "" ()))
    ("putc_unlocked" . #((213 4 4 108) "" ()))
    ("putchar" . #((213 4 4) "" ()))
    ("putchar_unlocked" . #((213 4 4) "" ()))
    ("puts" . #((213 4 108) "" ()))
    ("putw" . #((213 4 4 108) "" ()))
    ("r32value" . #((213 1 108) "" ()))
    ("r64value" . #((213 0 108) "" ()))
    ("raise" . #((213 4 4) "" ()))
    ("rand" . #((213 4) "" ()))
    ("realloc" . #((213 108 108 2) "" ()))
    ("register_for_window_events" . #((213 4) "" ()))
    ("xtm_set_main_callback" . #((213 -1 108) "" ()))
    ("remainder" . #((213 0 0 0) "" ()))
    ("remainderf" . #((213 1 1 1) "" ()))
    ("remove" . #((213 4 108) "" ()))
    ("remquo" . #((213 0 0 0 108) "" ()))
    ("remquof" . #((213 1 1 1 108) "" ()))
    ("rename" . #((213 4 108 108) "" ()))
    ("rewind" . #((213 -1 108) "" ()))
    ("rint" . #((213 4 0) "" ()))
    ("rintf" . #((213 4 1) "" ()))
    ("rmatch" . #((213 10 108 108) "" ()))
    ("rmatches" . #((213 2 108 108 208 2) "" ()))
    ("rreplace" . #((213 108 108 108 108 108) "" ()))
    ("rsplit" . #((213 10 108 108 108 108) "" ()))
    ("scalbn" . #((213 0 0 4) "" ()))
    ("scalbnf" . #((213 1 1 4) "" ()))
    ("sscanf" . #(varargs "" ())) ;; libc
    ("setbuf" . #((213 -1 108 108) "" ()))
    ("setenv" . #((213 4 108 108 4) "" ()))
    ("setjmp" . #((213 4 108) "" ()))
    ("setvbuf" . #((213 4 108 108 4 2) "" ()))
    ("sinh" . #((213 0 0) "" ())) ;; libm
    ("sinhf" . #((213 1 1) "" ())) ;; libm
    ("sprintf" . #(varargs "" ())) ;; libc
    ("strcat" . #((213 108 108 108) "" ()))
    ("strchr" . #((213 108 108 4) "" ()))
    ("strcmp" . #((213 4 108 108) "" ()))
    ("strcoll" . #((213 4 108 108) "" ()))
    ("strcpy" . #((213 108 108 108) "" ()))
    ("strcspn" . #((213 2 108 108) "" ()))
    ("strdup" . #((213 108 108) "" ()))
    ("strerror" . #((213 108 4) "" ()))
    ("string_hash" . #((213 2 108) "" ()))
    ("string_value" . #((213 108 108) "" ()))
    ("strlen" . #((213 2 108) "" ()))
    ("strncat" . #((213 108 108 108 2) "" ()))
    ("strncmp" . #((213 4 108 108 2) "" ()))
    ("strncpy" . #((213 108 108 108 2) "" ()))
    ("strpbrk" . #((213 108 108 108) "" ()))
    ("strrchr" . #((213 108 108 4) "" ()))
    ("strspn" . #((213 2 108 108) "" ()))
    ("strstr" . #((213 108 108 108) "" ()))
    ("strtok" . #((213 108 108 108) "" ()))
    ("strtok_r" . #((213 108 108 108 208) "" ()))
    ("strxfrm" . #((213 2 108 108 2) "" ()))
    ("swap32f" . #((213 4 1) "" ()))
    ("swap32i" . #((213 4 4) "" ()))
    ("swap64f" . #((213 2 0) "" ()))
    ("swap64i" . #((213 2 2) "" ()))
    ("sys_sharedir" . #((213 108) "" ()))
    ("sys_slurp_file" . #((213 108 108) "" ()))
    ("system" . #((213 4 108) "" ()))
    ("tan" . #((213 0 0) "" ())) ;; libm
    ("tanf" . #((213 1 1) "" ())) ;; libm
    ("tanh" . #((213 0 0) "" ())) ;; libm
    ("tanhf" . #((213 1 1) "" ())) ;; libm
    ("tempnam" . #((213 108 108 108) "" ()))
    ("tgamma" . #((213 0 0) "" ()))
    ("tgammaf" . #((213 1 1) "" ()))
    ("thread_fork" . #((213 108 108 108) "" ()))
    ("thread_destroy" . #((213 -1 108) "" ()))
    ("thread_join" . #((213 4 108) "" ()))
    ("thread_kill" . #((213 4 108) "" ()))
    ("thread_self" . #((213 108) "" ()))
    ("thread_sleep" . #((213 2 2 2) "" ()))
    ("thread_equal" . #((213 4 108 108) "" ()))
    ("thread_equal_self" . #((213 4 108) "" ()))
    ("tmpfile" . #((213 108) "" ()))
    ("tmpnam" . #((213 108 108) "" ()))
    ("trunc" . #((213 0 0) "" ()))
    ("ui16tod" . #((213 0 6) "" ()))
    ("ui16tof" . #((213 1 6) "" ()))
    ("ui1tod" . #((213 0 10) "" ()))
    ("ui1tof" . #((213 1 10) "" ()))
    ("ui32tod" . #((213 0 4) "" ()))
    ("ui32tof" . #((213 1 4) "" ()))
    ("ui64tod" . #((213 0 2) "" ()))
    ("ui64tof" . #((213 1 2) "" ()))
    ("ui8tod" . #((213 0 8) "" ()))
    ("ui8tof" . #((213 1 8) "" ()))
    ("ungetc" . #((213 4 4 108) "" ()))
    ("unsetenv" . #((213 4 108) "" ()))
    ("unswap32f" . #((213 1 4) "" ()))
    ("unswap32i" . #((213 4 4) "" ()))
    ("unswap64f" . #((213 0 2) "" ()))
    ("unswap64i" . #((213 2 2) "" ()))
))
# File Utilities
(define-macro (unix-or-Windows unix-expr win-expr)
  (if (string=? (sys:platform) "Windows")
      win-expr unix-expr))

(define Windows-convert-unix-path
  (lambda (unix-path)
    (regex:replace-all unix-path  "/" "\\")))

(define sanitize-platform-path
  (lambda (path)
    (if (string=? (sys:platform) "Windows")
        (Windows-convert-unix-path path)
        path)))

(define Windows-add-libdir-to-PATH
  (lambda ()
    (let ((path (sys:command-output "echo %PATH%")))
      (if (not (string-contains? path "libs/platform-shlibs"))
(sys:set-env "PATH" (string-append path ";" (sys:share-dir) "/libs/platform-shlibs")

* Memzones

(define icr:new-zone
  (lambda args
    (if (null? args)
        (sys:create-mzone *impc:default-zone-size*)
        (sys:create-mzone (car args)))))

(define icr:destroy-zone
  (lambda (zone)
    (if (equal? *impc:zone* zone)
        (set! *impc:zone* (sys:default-mzone)))
    (if (equal? zone (sys:default-mzone))
        (print-notification "You are not allowed to destroy the default zone")
        (sys:destrop-mzone zone))))

(define icr:set-zone
  (lambda (zone)
    (set! *impc:zone* zone)))

(define icr:set-zone-default
  (lambda ()
    (set! *impc:zone* (sys:default-mzone))))

## letz
(letz 100000 ((a 3)                  ;; 3 is bound to a
              (b 42)                 ;; 42 is bound to b
              (c:float* (alloc 10))) ;; a pointer to enough memory for 10 floats is bound to c
  (+ a b (ftoi64 (pref c 0))))

`letz' is the same as `let', with the addition of the new memzone"
'(bindings [zone-size] body))

(define impc:ti:zone_cleanup
  (lambda (ast)
    `(let ((zone (llvm_peek_zone_stack))
           (hooks:<i64,i8*,i8*>* (cast (tref zone 4)))
           (hook:<i64,i8*,i8*>* (alloc))
           (f (lambda () ,@(cdr ast) void)))
       (tfill! hook 0 (cast f i8*) (cast hooks i8*))
       (tset! zone 4 (cast hook i8*))
void)))

# Loops
(define impc:ti:gteq
  (lambda (ast)
    `(or (> ,(cadr ast) ,(caddr ast))
         (= ,(cadr ast) ,(caddr ast)))))

(define impc:ti:lteq
  (lambda (ast)
    `(or (< ,(cadr ast) ,(caddr ast))
         (= ,(cadr ast) ,(caddr ast)))))


;; This to auto surround dotimes with a let
(define impc:ti:doloop
  (lambda (ast inbody?)
    ;; (println 'doloop 'ast: ast)
    (let* ((pair (regex:type-split (symbol->string (caadr ast)) ":"))
           (sym (string->symbol (car pair))))
      `(let ((,(caadr ast) (bitconvert 0)))
         (begin
           (dotimes
               ,(if (null? (cddr (cadr ast)))
                    `(,sym ,(impc:ti:first-transform (cadr (cadr ast)) inbody?))
                    `(,sym ,(impc:ti:first-transform (cadr (cadr ast)) inbody?)
                           ,(impc:ti:first-transform (caddr (cadr ast)) inbody?)))
             (begin ,@(impc:ti:first-transform (cddr ast) inbody?))))))))

(impc:ti:register-new-builtin
 "doloop"
 ""
"doloop

Execute `body' forms `count' times, with `index-variable' bound to
successive numerical values (incrementing by 1 each loop). If `start'
is given, start from there, otherwise start from 0.

`index-variable' will be automatically bound as a temporary variable
of type i32, i64, float or double - the type will be inferred from the
types of `start' and `count'"
 '(index-variable [start] count body))

(define impc:ti:dotimes
  (lambda (ast inbody?)
    (list 'dotimes
          (impc:ti:first-transform (cadr ast) inbody?)
          (cons 'begin (impc:ti:first-transform (cddr ast) inbody?)))))


(impc:ti:register-new-builtin
 "dotimes"
 ""
 "dotimes loop

Execute `body' forms `count' times, with `index-variable' bound to
successive numerical values (incrementing by 1 each loop). If `start'
is given, start from there, otherwise start from 0.

`index-variable' can be either i32, i64, float or double, and must be
defined outside the loop. For a loop where the index variable is
automatically bound as a temporary variable, see `doloop'."
 '(index-variable [start] count body))


(define impc:ti:while
  (lambda (ast inbody?)
    (list 'while
          (impc:ti:first-transform (cadr ast) inbody?)
          (cons 'begin (impc:ti:first-transform (cddr ast) inbody?)))))

(impc:ti:register-new-builtin
 "while"
 ""
 "while loop

Continue executing `body' forms until `test-expression' returns #f"
'(test-expression body))


# Built Ins
(define *impc:mathintrinsicslist* '(sin cos ceil floor exp pow log log2 log10 sqrt fabs round trunc nearbyint fma exp2 powi))
(define *impc:mathbinaryaritylist* '(* - / + % modulo bitwise-and bitwise-or bitwise-eor bitwise-shift-left bitwise-shift-right))
(define *impc:lambdaslist* '(lambda lambdas lambdaz lambdah))

(define impc:ti:first-transform
  (lambda (ast inbody?)
    ;; (println 'ast: ast)
    (if (null? ast) '()
        (cond ((list? ast)
               (cond ((or (and (symbol? (car ast))
                               (impc:ti:get-polyfunc-candidate-types (symbol->string (car ast))))
                          (impc:ti:genericfunc-exists? (car ast)))
                      (set! *unique-polynum* (+ 1 *unique-polynum*))
                      (cons (string->symbol (string-append (symbol->string (car ast))
                                                           "##" ;"$$$"
                                                           (number->string *unique-polynum*)))
                            (impc:ti:first-transform (cdr ast) inbody?)))
                     ((and ;; exact poly match (with type)
                       (symbol? (car ast))
                       (regex:match? (symbol->string (car ast)) ":\\[")
                       ;;(impc:ti:polyfunc-exists? (car (regex:type-split (symbol->string (car ast)) ":"))
                       (impc:ti:get-polyfunc-candidate (car (regex:type-split (symbol->string (car ast)) ":"))
                                                       (impc:ir:get-type-from-pretty-str
                                                        (cadr (regex:type-split (symbol->string (car ast)) ":")))))
                      (let ((p (regex:type-split (symbol->string (car ast)) ":")))
                        (cons
                         (impc:ti:get-polyfunc-candidate (car p)
                                                         (impc:ir:get-type-from-pretty-str (cadr p)))
                         (impc:ti:first-transform (cdr ast) inbody?))))
                     ((and ;; generic match (with type)
                       (symbol? (car ast))
                       (regex:match? (symbol->string (car ast)) ":\\[")
                       (impc:ti:genericfunc-exists? (car (regex:type-split (symbol->string (car ast)) ":"))))
                      (let* ((p (regex:type-split (symbol->string (car ast)) ":"))
                             (ptrdepth (impc:ir:get-ptr-depth (cadr p))))
                        (impc:ti:specialize-genericfunc (car p) (cadr p))
                        (cons
                         (string->symbol (impc:ir:pointer++ (string-append (car p) "_poly_" (cname-encode (cadr p))) (- ptrdepth 1)))
                         (impc:ti:first-transform (cdr ast) inbody?))))
                     ((and ;; non exact poly match with (with type)
                       (symbol? (car ast))
                       (regex:match? (symbol->string (car ast)) ":\\[")
                       (impc:ti:polyfunc-exists? (car (regex:type-split (symbol->string (car ast)) ":"))))
                      (let* ((p (regex:type-split (symbol->string (car ast)) ":"))
                             (t (if (impc:ti:typealias-exists? (cadr p))
                                    (impc:ti:get-typealias-type (cadr p))
                                    (cadr p)))
                             (cname (cname-encode (impc:ir:get-base-type t)))
                             (ptrdepth (impc:ir:get-ptr-depth t)))
                        (cons
                         (string->symbol (string-append (car p) "_adhoc_" cname))
                         (impc:ti:first-transform (cdr ast) inbody?))))
                     ((eq? (car ast) 'letz)
                      (impc:ti:first-transform (impc:ti:letz ast) inbody?))
                     ((eq? (car ast) 'memzone)
                      (impc:ti:first-transform (impc:ti:memzone ast) inbody?))
                     ((eq? (car ast) 'beginz)
                      (impc:ti:first-transform (impc:ti:beginz ast) inbody?))
                     ((eq? (car ast) 'zone_cleanup)
                      (impc:ti:first-transform (impc:ti:zone_cleanup ast) inbody?))
                     ((eq? (car ast) '>=)
                      (impc:ti:first-transform (impc:ti:gteq ast) inbody?))
                     ((eq? (car ast) '<=)
                      (impc:ti:first-transform (impc:ti:lteq ast) inbody?))
                     ((eq? (car ast) 'and)
                      (impc:ti:first-transform (impc:ti:and (cdr ast)) inbody?))
                     ;; ((eq? (car ast) 'random)
                     ;;  (impc:ti:first-transform (impc:ti:random (cdr ast)) inbody?))
                     ((eq? (car ast) 'quote)
                      (impc:ti:first-transform (impc:ti:quote (cadr ast)) inbody?))
                     ((eq? (car ast) 'list)
                      (impc:ti:first-transform (impc:ti:list (cdr ast)) inbody?))
                     ((or (eq? (car ast) 'strln)
                          (eq? (car ast) 'strj))
                      (impc:ti:first-transform (impc:ti:format (cdr ast)) inbody?))
                     ((eq? (car ast) 'sprintln)
                      (impc:ti:first-transform (impc:ti:sprintln (cdr ast)) inbody?))
                     ((eq? (car ast) 'sprintout)
                      (impc:ti:first-transform (impc:ti:sprintln2 (cdr ast)) inbody?))
                     ((eq? (car ast) 'println)
                      (impc:ti:first-transform (impc:ti:println (cdr ast)) inbody?))
                     ((eq? (car ast) 'printout)
                      (impc:ti:first-transform (impc:ti:println2 (cdr ast)) inbody?))
                     ((eq? (car ast) 'afill!)
                      (impc:ti:first-transform (impc:ti:afill! (cdr ast)) inbody?))
                     ((eq? (car ast) 'pfill!)
                      (impc:ti:first-transform (impc:ti:pfill! (cdr ast)) inbody?))
                     ((eq? (car ast) 'tfill!)
                      (impc:ti:first-transform (impc:ti:tfill! (cdr ast)) inbody?))
                     ((eq? (car ast) 'vfill!)
                      (impc:ti:first-transform (impc:ti:vfill! (cdr ast)) inbody?))
                     ((eq? (car ast) 'or)
                      (impc:ti:first-transform (impc:ti:or (cdr ast)) inbody?))
                     ((eq? (car ast) 'free)
                      (list 'free (list 'bitcast (impc:ti:first-transform (cadr ast) inbody?)
                                        'i8*)))
                     ((member (car ast) '(vector_ref))
                      (impc:ti:first-transform `(let ((v1 (alloc)) (v2 (vector ,@(cdr ast)))) (pset! v1 0 v2) v1) inbody?))
                     ((member (car ast) '(array_ref))
                      (impc:ti:first-transform `(let ((a1 (alloc)) (a2 (array ,@(cdr ast)))) (pset! a1 0 a2) a1) inbody?))
                     ((member (car ast) '(tuple_ref))
                      (impc:ti:first-transform `(let ((t1 (alloc)) (t2 (tuple ,@(cdr ast)))) (pset! t1 0 t2) t1) inbody?))
                     ((member (car ast) '(vector))
                      `(make-vector ,@(map (lambda (x) (impc:ti:first-transform x inbody?)) (cdr ast))))
                     ((member (car ast) '(array))
                      `(make-array ,@(map (lambda (x) (impc:ti:first-transform x inbody?)) (cdr ast))))
                     ((member (car ast) '(tuple))
                      `(make-tuple ,@(map (lambda (x) (impc:ti:first-transform x inbody?)) (cdr ast))))
                     ((eq? (car ast) 'not)
                      (impc:ti:first-transform (impc:ti:not (cadr ast)) inbody?))
                     ((member (car ast) '(callback schedule))
                      (impc:ti:first-transform (impc:ti:callback (impc:ti:first-transform (cdr ast) inbody?)) inbody?))
                     ((and (member (car ast) *impc:mathbinaryaritylist*)
                           (<> (length ast) 3))
                      (impc:ti:first-transform (impc:ti:binary-arity ast inbody?) inbody?))
                     ((member (car ast) '(bitwise-not ~))
                      (impc:ti:bitwise-not-to-eor ast inbody?))
                     ((member (car ast) *impc:lambdaslist*)
                      (if inbody?
                          (impc:ti:lambda ast)
                          (cons (impc:ti:first-transform (car ast) inbody?)
                                (cons (impc:ti:first-transform (cadr ast) #t)
                                      (list (cons 'begin (impc:ti:first-transform (cddr ast) #t)))))))
                     ((eq? (car ast) 'cond)
                      (impc:ti:first-transform (impc:ti:cond (cdr ast)) inbody?))
                     ((eq? (car ast) 'cset!)
                      (list 'closure-set!
                            (impc:ti:first-transform (cadr ast) inbody?)
                            (symbol->string (caddr ast))
                            (impc:ti:first-transform (cadddr ast) inbody?)
                            (if (not (null? (cddddr ast)))
                                (impc:ir:get-type-str (impc:ir:convert-from-pretty-types (car (cddddr ast)))))))
                     ((eq? (car ast) 'cref)
                      (list 'closure-ref
                            (impc:ti:first-transform (cadr ast) inbody?)
                            (symbol->string (caddr ast))
                            (if (not (null? (cdddr ast)))
                                (impc:ir:get-type-str (impc:ir:convert-from-pretty-types (cadddr ast))))))
                     ((eq? (car ast) 'refcheck)
                      (list 'closure-refcheck
                            (impc:ti:first-transform (cadr ast) inbody?)
                            (symbol->string (caddr ast))))
                     ((member (car ast) '(cast convert))
                      (if (= (length ast) 2)
                          (impc:ti:first-transform (list (if (eq? (car ast) 'cast)
                                                             'bitcast
                                                             'bitconvert)
                                                         (cadr ast)) inbody?)
                          (let* ((p (regex:type-split (symbol->string (caddr ast)) ":"))
                                 (ptrdepth (impc:ir:get-ptr-depth (caddr ast)))
                                 (basetype (if (null? (cdr p)) #f (impc:ir:get-base-type (cadr p))))
                                 (etype (if (null? (cdr p)) #f (cname-encode basetype))))
                            (impc:ti:first-transform
                             (list (if (eq? (car ast) 'cast)
                                       'bitcast
                                       'bitconvert)
                                   (cadr ast)
                                   (if etype
                                       (string->symbol
                                        (impc:ir:pointer++ (string-append "%" (car p) "_poly_" etype)
                                                           ptrdepth))
                                       (string->symbol (car p))))
                             inbody?))))
                     ((eq? (car ast) 'doloop) (impc:ti:doloop ast inbody?))
                     ((eq? (car ast) 'dotimes) (impc:ti:dotimes ast inbody?))
                     ((eq? (car ast) 'while) (impc:ti:while ast inbody?))
                     ((member (car ast) *impc:letslist*)
                      (cons (impc:ti:first-transform (car ast) inbody?)
                            (cons (map (lambda (p)
                                         (list (impc:ti:first-transform (car p) #f)
                                               (impc:ti:first-transform (cadr p) #f))
                                         )
                                       (cadr ast))
                                  (list (cons 'begin (impc:ti:first-transform (cddr ast) #t))))))
                     ((and (symbol? (car ast))
                           (regex:match? (symbol->string (car ast)) ".*\\..*")
                           (not (regex:match? (symbol->string (car ast)) "\\.[0-9]*i$"))
                           ;; this last case here to catch of '.' in
                           ;; floating point numbers of type 1.000:float etc..
                           (not (number? (string->atom (car (regex:type-split (symbol->string (car ast)) ":"))))))
                      (if (regex:match? (symbol->string (car ast)) ".*\\..*:.*")
                          (let* ((subs (regex:split (symbol->string (car ast)) "\\."))
                                 (a (string->symbol (car subs)))
                                 (subs2 (regex:type-split (car (reverse subs)) ":"))
                                 (b (string->symbol (car subs2)))
                                 (c (string->symbol (cadr subs2))))
                            (cond ((and (= (length ast) 1) (= (length subs) 2)) ;; cref
                                   (impc:ti:first-transform (list 'cref a b c) inbody?))
                                  ((= (length subs) 2) ;; cset
                                   (impc:ti:first-transform (list 'cset! a b (cadr ast) c) inbody?))
                                  ((and (> (length subs) 2) (= (length ast) 2)) ;; multipart cset
                                   (impc:ti:first-transform
                                    (impc:ti:multicset
                                     (append (map (lambda (x) (string->symbol x))
                                                  (append (reverse (cdr (reverse subs))) subs2))
                                             (cdr ast)))
                                    inbody?))
                                  ((and (> (length subs) 2) (= (length ast) 1)) ;; multipart cref
                                   (impc:ti:first-transform
                                    (impc:ti:multicref
                                     (map (lambda (x) (string->symbol x))
                                          (append (reverse (cdr (reverse subs))) subs2)))
                                    inbody?))
                                  (else ;; error!
                                   (impc:compiler:print-compiler-error "Bad form!" ast))))
                          (let* ((subs (regex:split (symbol->string (car ast)) "\\."))
                                 (a (string->symbol (car subs)))
                                 (b (string->symbol (cadr subs))))
                            (if (= (length ast) 1)
                                (impc:ti:first-transform (list 'cref a b) inbody?)
                                (impc:ti:first-transform (list 'cset! a b (cadr ast)) inbody?)))))
                     ((and (atom? (car ast))
                           (symbol? (car ast))
                           (impc:ti:xtmacro-exists? (symbol->string (car ast))))
                      (impc:ti:first-transform
                       (macro-expand (cons (string->symbol
                                            (string-append "xtmacro_"
                                                           (symbol->string (car ast))))
                                           (cdr ast)))
                       'inbody?))
                     (else
                      (cons ;(impc:ti:first-transform (car ast) inbody?)
                       (impc:ti:first-transform (car ast) #t)
                                        ;(impc:ti:first-transform (cdr ast) inbody?)))))
                       (impc:ti:first-transform (cdr ast) #t)))))
              (else
               ;; (println 'atom: ast)
               (cond ((rational? ast)
                      (impc:ti:first-transform `(Rat ,(rational->n ast) ,(rational->d ast)) inbody?))
                     ((eq? ast #f) '(impc_false))
                     ((eq? ast #t) '(impc_true))
                     ((eq? ast '&) 'bitwise-and)
                     ((eq? ast 'bor) 'bitwise-or) ; can't use a pipe
                     ((eq? ast '^) 'bitwise-eor)
                     ((eq? ast '<<) 'bitwise-shift-left)
                     ((eq? ast '>>) 'bitwise-shift-right)
                     ((eq? ast '~) 'bitwise-not)
                     ((eq? ast 'else) '(impc_true))
                     ((eq? ast 'null) '(impc_null))
                     ((eq? ast 'now) 'llvm_now)
                     ((eq? ast 'pset!) 'pointer-set!)
                     ((eq? ast 'pref) 'pointer-ref)
                     ((eq? ast 'pref-ptr) 'pointer-ref-ptr)
                     ((eq? ast 'vset!) 'vector-set!)
                     ((eq? ast 'vref) 'vector-ref)
                     ((eq? ast 'vshuffle) 'vector-shuffle)
                     ((eq? ast 'aset!) 'array-set!)
                     ((eq? ast 'aref) 'array-ref)
                     ((eq? ast 'aref-ptr) 'array-ref-ptr)
                     ((eq? ast 'tset!) 'tuple-set!)
                     ((eq? ast 'tref) 'tuple-ref)
                     ((eq? ast 'tref-ptr) 'tuple-ref-ptr)
                     ((eq? ast 'salloc) 'stack-alloc)
                     ((eq? ast 'halloc) 'heap-alloc)
                     ((eq? ast 'zalloc) 'zone-alloc)
                     ((eq? ast 'alloc) 'zone-alloc)
                     ;; ((eq? ast 'schedule) 'callback)
                     ((eq? ast 'randomf) 'imp_randf)
                     ((eq? ast 'void) '(void))
                     ((and (symbol? ast)
                           (regex:match? (symbol->string ast) "^[+-]?[0-9]*\\.?[0-9]*[+-][0-9]*\\.?[0-9]*i$"))
                      (let ((p (regex:matched (symbol->string ast) "^([+-]?[0-9]*\\.?[0-9]*)([+-][0-9]*\\.?[0-9]*)i$")))
                        ;;`(Cpxd ,(* 1.0 (string->number (cadr p))) ,(* 1.0 (string->number (caddr p))))))
                        (impc:ti:first-transform `(Cpxd ,(* 1.0 (string->number (cadr p))) ,(* 1.0 (string->number (caddr p)))) inbody?)))
                     ((and (symbol? ast)
                           (regex:match? (symbol->string ast) ":\\$(\\[|<)"))
                      (let ((t (impc:ti:expand-generic-type ast)))
                        (if (impc:ti:closure-exists? (symbol->string t))
                            t
                            (let ((p (regex:type-split (symbol->string t) "_poly_")))
                              (impc:ti:specialize-genericfunc (car p) (cname-decode (cadr p)))
                              t))))
                     ((and (symbol? ast)
                           (regex:match? (symbol->string ast) ":(f)|(i)|(f32)|(f64)|(float)|(double)|(i1)|(i8)|(i64)|(i32)|(i64)"))
                      (let ((p (regex:type-split (symbol->string ast) ":")))
                        (if (not (number? (string->atom (car p))))
                            ast
                            ;; otherwise do a convert
                            (cond ((string=? (cadr p) "f")
                                   (list 'bitconvert (string->atom (car p)) 'float))
                                  ((string=? (cadr p) "i")
                                   (list 'bitconvert (string->atom (car p)) 'i32))
                                  ((string=? (cadr p) "f32")
                                   (list 'bitconvert (string->atom (car p)) 'float))
                                  ((string=? (cadr p) "f64")
                                   (list 'bitconvert (string->atom (car p)) 'double))
                                  (else
                                   (list 'bitconvert (string->atom (car p)) (string->symbol (cadr p))))))))
                     (else ast)))))))



# String Manipulation
;; regex:type-split pair is like regex split
;; but only splits on 'first' occurence
(define regex:type-split
  (lambda (str char)
    (let ((p (regex:split str char)))
      (if (and (> (length p) 1)
               (> (length (cdr p)) 1))
          (list (car p) (apply string-append (cadr p)
                               (map (lambda (k) (string-append char k)) (cddr p))))
p))))

# Regex

(define regex:replace-all
  (lambda (str replace with)
    (if (regex:match? str replace)
        (regex:replace-all (regex:replace str replace with) replace with)
        str)))

;; where finds and replaces
;; are equal length lists
(define regex:replace-everything
  (lambda (str finds replaces)
    (if (<> (length finds) (length replaces))
        (impc:compiler:print-compiler-error "regex:replace-everything expects an equal number of finds and replaces"))
    (for-each (lambda (find replace)
                (if (not (string=? find replace))
                    (let ((s (regex:replace-all str find replace)))
                      (set! str s))))
              finds replaces)
str))

# Load a library
(define-macro (bind-dylib library lib-path)
  (let ((path (eval lib-path)))
    (if (string? path)
        (set! path (list path)))
    (impc:aot:insert-load-dylib-details library path)
`(impc:ti:bind-dylib ',library ',path)))


(impc:ti:register-new-builtin
 "bind-dylib"
 ""
 "load a dynamic library

e.g.

(bind-dylib lib \"libGL.so\")

@param lib-symbol - symbol to refer to the library
@param lib-paths - a string (or list of strings) of paths to search for the dylib"
'(lib-symbol lib-paths))



(impc:ti:register-new-builtin
 "bind-lib"
 ""
 "bind a C function from a shared library"
 '(libname function-name type optional-docstring))



unbind-func symname



;; this here for binding to CLOSURE in dylib
;;
;; arg is for *optional* zone size arg
(define-macro (bind-lib-func library symname type zone-size docstring body)



;; THIS IS A HELPER FUNCTION
;;
;; returns a (bind-lib-xtm) form for the named function
;; by using the xtm-closure-doc to get the type
;; function must already have been compiled into module
(define-macro (bind-lib-xtm-get-string name)
  (let ((res (eval `(xtm-closure-doc ,name))))
    (if (string? res)
        `(sexpr->string '(bind-lib-xtm mathlib ,name ,(string->symbol res)))
        `(sexpr->string '(bind-lib-xtm mathlib ,name ,(string->symbol (cdr res)))))))


;; Wrap a native, bound C function, allowing it to be called from scheme
(define-macro (bind-wrapper local-sym native-sym)
  (let* ((types (cdr (impc:ti:get-closure-arg-types (symbol->string native-sym))))
         (args (map (lambda (t v) v)
                    types (make-list-with-proc
                           (length types)
                           (lambda (i)
                             (string->symbol (string-append "arg_" (atom->string i))))))))
    `(bind-func ,local-sym
       (lambda ,args
,(cons native-sym args)))))


# xtm-doc stuff
Don't really know how that is supposed to work. But could be useful.

