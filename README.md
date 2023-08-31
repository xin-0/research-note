# research-note

The complete note consists of **two** parts:
- Input Source
- Knowledge Map

## Design goal
### Input Source
Notes in this **should satisfy**:
1. Locality: Can focus on the current material without think about the knowledge map. Little or none overhead during note-taking stage.
2. Context Providing: Preserve the structure of the input source when digesting a certain material. Provide the learning context that will be helpful when reviewing.

Notes in this **are** notes taken when:
1. read a textbook
2. read a paper
3. watch youtube academic talks

### Knowledge Map
Notes in this **should satisfy**:
1. Concept based
2. Traceable: a key statement can be traced back to the input material it came from.

Notes in this **are**:
1. Individual concepts

## Structure Sketch

![strucure|600](media/imgs/structure.png)
Knowledge Map is supposed to arise from input source. "Other app" can help with processing the input source but not modifying directly on the knowledge base.
## Raw Data
Raw data are individual notes simply put under `/source` or `/knowledge` 
## Augmentation
For gaining insight from the immense knowledge base, raw data need to be augmented with data structures.
### folder
Folder gives **tree** structure on the files. Under `/source`, input source like textbooks will be naturally organized by folders since most books are written chapter by chapter. For files in `/knowledge`, such tree structure can be helpful when context is needed for different concepts share the same name.
### obsidian
[Obsidian](https://obsidian.md) is chosen for its ability of building and showing linked notes as a graph. Very handy for building the knowledge map. **Graph** in obsidian is great for showing connection between contents. And tag can be utilized to give **set** structure on files, which is looser than tree or graph.
### git
Use git to keep track of the changing history thus grant the database structure along **time**. such history is useful especially for concepts in the knowledge map. By checking the file history, we can know how the concept becomes the way it is now.

### with other apps
For example, can use [zotero](https://www.zotero.org) for annotating and organizing papers.