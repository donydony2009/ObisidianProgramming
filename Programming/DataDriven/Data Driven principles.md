
##### Introduction
Data driven is the antithesis of most other programming languages. The technique does not model the problem domain. **It does not promote mapping the problem to the program.**

Heavy paradigms that try to map to the problem domain, pretend that the CPU architecture doesn't exist. **They abstract the idea of bytes and CPU pipelines**

**Data is data**. And data manipulation is data manipulation. The fancy objects of OOP are just a way from programmers to reason. But ultimately as things change it proves to just be **needless limitations that don't need to be there**

Data driven design **deals better with change** because there is less structure, less implied rules about how the data should behave.  You can more easily change things when you are not tied to the OOP architecture you initially chose for the initial design. You just need to change the data or the data manipulation to fit the current design.

But because there is less structure to your data it can be harder to reason about it. Harder to track where everything is.

##### Data grouping
Data should be grouped. Hot data should be next to hot data, cold with cold. This avoids cache misses and greatly speeds up runtime.

OOP hinders this because usually all data data related to an object is inside that object. Often this means both hot data and cold data.

##### Data manipulation can be reused
If all you have is data and data manipulation, data manipulation can be reused more easily no matter the context if it fits