# Packilog Manifest Format

This document describes the format of the `packilog.json` manifest files. This format is a work in progress, please submit feedback via github issues or pull requests!

## Top level object

All Packilog manifest files should be valid JSON, with a JSON object as the root. Currently there are two supported members of this root object, `files` and `dependencies`.

```json
{
    "files":
    [
        "olde_school.v",
        "fancy.sv"
    ],
    "dependencies":
    [
        {
            "type": "file",
            "source": "http://awesome.verilog.source/somethingcool.sv",
            "filename": "somethingawesome.sv"
        }
    ]
```

## Files list

For Packilog packages, the `files` member should be a list of relative files to include when someone uses that package as a dependency. These files will be copied into the directory the `packilog` script is ran from.

## Dependencies list

The `dependencies` member should be a list of JSON objects that describe the various dependencies. All of these objects should have a `type` member the determines what type of packing is referenced and what dependecy handler should be used. Additional members of the object depend on the dependency type.

### File type dependency

The `file` type dependency simply pulls in a file from a remote resource. It requires two additional object members, `source` and `filename`.

The `source` member is a URL that points to the file that should be included in the project.

The `filename` member is the filename that the source code should be saved as.

### Package URL type dependency

The `packageurl` type dependency pulls in a package from a remote URL. It requires a `source` object member.

The `source` member is a URL path to a Packilog package, the dependency handler will look for a `packilog.json` manifest file relative to the path specified, then pull in code based on the contents of that manifest.
