CMake markdown to html converter (pandoc)
=========================================

This is a small CMake helper script to 
create html files from markdown.

## Usage

If you include the `pandoc-helper` it provides the 
`covert_md_to_html(TARGETNAME PANDOC_ARGUMENTS LIST_MD_FILES)` function.

* TARGETNAME: The name of the custom target
* PANDOC_ARGUMENTS: All additional arguments for `pandoc`
* LIST_MD_FILES: A CMake list of markdown files ending in `.md`. Relative to the current source directory.

## Example

```
include(pandoc-helper)
set(doc_resources index.md example.md)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/resources/style.css ${CMAKE_CURRENT_BINARY_DIR}/style.css COPYONLY)
covert_md_to_html(mytarget "--css=style.css --include-after-body=${CMAKE_CURRENT_SOURCE_DIR}/resources/footer.html" "${doc_resources}")
add_dependencies(doc mytarget)
```