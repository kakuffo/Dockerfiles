
# Continues improvement in DevOps

As a DevOps Engineer, apart from progressing my daily task in a sprint, I enjoy the process of seeking, and identifying 
improvement opportunities within the DevOps artefacts.  This process for me grew from heuristics and has grown into a 
well-defined process which I apply continually.  The approach is loosely based on the exploratory testing, and the 
technique is framed around the exploratory testing charter technique.  I first identify the scope for exploration; 
for example, Dockerfiles and JenkinsFiles.  I then research, the scope widely to identify improvement opportunities, 
such as the Source lines of code (SLOC) for a dockerfile.

## Source line of code tools

### MacOS (Homebrew)

```Shell
$ brew install tokei
```

## Dockerfile optimisation

a command that changes the file system, it adds a new layer.
Expand  built-in labels to include important information related
Use key-value pairs for entry input. For example, to input a description, enter:



```JSON
     "Labels":  {
     "maintainer": "kakuffo@apertusdatum"
     "description": "This text illustrates that label-values can span"
      }
```
      
```Shell
CMD apt-get update
CMD apt-get upgrade
CMD apt-get install apache2
```

To create them in one layer, combine the commands as follows:

```Shell
CMD apt-get update && apt-get upgrade -y && apt-get install apache2 -y
```

It's also possible to split long commands across several lines by including \\ at the end of the line; write the next part of the command on the following line:

```Shell
     CMD apt-get update \\
          && apt-get upgrade -y \\
          && apt-get install apache2 -y
````