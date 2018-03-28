from: http://architects.dzone.com/articles/humble-architects, written by Johannes Brodwall
Rule 5: Tactical reuse in across systems is suboptimization

Reuse creates coupling. If system X and system Y reuse some functionality and system X needs that functionality to be modified, this will affect system Y. At the very least, the team working on system X must decide to make a private fork of the reused functionality, which means that it’s no longer really reused. At worst, system Y will get a bug because of a change in the reused functionality.
When you reuse across systems, what you reuse should either be stable (say: the Java SE platform, or something so stable that you definitely didn’t make it yourself) or strategic. By strategic reuse, I mean services that integrate information and not just duplicate functionality.
In other words: Reuse should either be use or integration. Duplication is your friend. 
