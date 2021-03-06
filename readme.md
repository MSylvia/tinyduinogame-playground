# Project purpose

Programming games for the TinyDuino system is a challenge. The severe 
limitations regarding RAM and flash memory makes it difficult to develop 
games with this system. 

The TinyScreen itself has a small resolution, however drawing to the screen
takes substantial amounts of time. Moreover, drawing has to happen one line
after another, all lines through from top to bottom. This property makes
it additionally complicated to draw on the screen in a flickerfree way.

*This project aims to require as little resources as possible while providing 
an interface to draw efficiently as well as easily on the screen.*

# Approach

* Include everything into the main file via #include
	* The compiler can optimize the code better when everything is in one file
	* The code execution is significantly faster - calling externally defined functions is expensive. Yes, this is a violation of common 
	  programming practices. The gained performance and memory saving however is worth the hazzle. 
* Avoid C++
	* ... I am simply not experienced enough at writing C++ code
	* it's easy to waste precious flash memory for a bit more comfort
	* I have saved quite some memory by porting existing code into plain C code, thus gaining the attitude that it might be worth the effort
* Declare functions as static - faster to call and smaller memory footprint

# Rendering engine

The most important aspect of this code is to provide a rendering engine. Being able
to draw shapes and texures on the TinyScreen is at the core of the code.

## Reason

The rendering works as it works because of the challenges that the TinyScreen API
is posing. 