
# Continues improvement in DevOps

As a DevOps Engineer, apart from progressing my daily task in a sprint, I enjoy the process of seeking, and identifying 
improvement opportunities within the DevOps artefacts.  This process for me grew from heuristics and has grown into a 
well-defined process which I apply continually.  The approach is loosely based on the exploratory testing, and the 
technique is framed around the exploratory testing charter technique.  I first identify the scope for exploration; 
for example, Dockerfiles and JenkinsFiles.  I then research, the scope widely to identify improvement opportunities, 
such as the Source lines of code (SLOC) for a dockerfile.

## Source line of code tools

### MacOS (Homebrew)

````Shell
$ brew install tokei
````

CMD apt-get update
CMD apt-get upgrade
CMD apt-get install apache2

To create them in one layer, combine the commands as follows:

CMD apt-get update && apt-get upgrade -y && apt-get install apache2 -y

It's also possible to split long commands across several lines by including \\ at the end of the line; write the next part of the command on the following line:

     CMD apt-get update \\
          && apt-get upgrade -y \\
          && apt-get install apache2 -y