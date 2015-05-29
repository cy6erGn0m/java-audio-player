# Required Java #

Library requires at least Java 5.

# Compile time #
Requires jar in classpath is:
`JavaMediaPlayer.jar`

# Runtime #
At runtime two jar's required:
`JavaMediaPlayer.jar`
`jl1.0.1.jar`

# Runnning on non-Sun JVM's #
Currently, it looks like GNU java can't use Java Sound, so, player crashes with internal NPE. JAMVM also shows message `NoClassDefFound` near library bouncycastle.

**TO BE DONE**
Investigation to be continued.