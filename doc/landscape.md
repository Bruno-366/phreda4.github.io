# Landscape

Simplicity is not a starting point, it requires analysis, testing and understanding. This language is made to find a simple solution to a problem, but this is not simple, try all ideas, usually the first ones are correct but, sometimes, you need a deeper knowledge or you can not see a certain part of it.

:r4 is brutally simple and therefore can be seen as something primitive, in fact someone can compare it with BF and maybe have a point of contact, but, although it seems otherwise, the idea is to simplify the development.

If something teaches forth is to distrust the preconceptions, anyone who learns FORTH would try to avoid the terrible gymnastics of controlling the data stack, many dialects immediately add the premises, only to save it's sport. Do not do it! The careful order that can be found from the data traveling from one word to the other is sometimes the key to everything, putting the name of the word is as important as finding the order of the parameters.

If you are in a hurry you can start by putting variables for any data and then find the way that these variables are combined in a place on the stack, sometimes I have put to translate code from C to :r4 and, although it is possible to do this translation almost without understanding what he is doing, as one sees that he is doing and manages to find a better way, the code begins to shrink.

It is preferable to recode that patching, but, rightly, FORTH has the ability to modify things at almost any level without requiring a big change, the absence of a legal language that defines what can be done and what does not, instead of complicating the development simplifies it.

Each system is composed of several levels, some closer to the machine and others more abstract, but beware! It is easy to define levels that are not necessary, overcomplicate and try to solve problems that do not exist are the worst mistakes one can make, Charles Mooro and Jeff Fox are clear about this, I strongly recommend reading everything they find about them.

When you think about :r4 I think that you are not aware of the real code that it generates, but I do, since my goal is to improve the language. I'm not sure if this can be seen for someone who does not think how is generating the code and for this I do explicit here: The most important abstraction is the address, the name of a direction can point to anything, a data, a code , a more complex structure, a drawing, etc ... this is the point of separation of language levels, where words are defined that build a level, for example at the level of bits, and then words that build above this level, for example a graphic icon.