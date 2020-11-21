![Algorithms](https://socialify.git.ci/codeiiest-dev/algorithms/image?description=1&font=Raleway&forks=1&issues=1&language=1&owner=1&pattern=Charlie%20Brown&pulls=1&stargazers=1&theme=Dark)

# About the Project

This repository contains some of the most  **intriguing and awesome algorithms**  of daily life implemented in languages primarily in C/C++/Java/Python.

## Project Details

The entire project is divided into 4 parts

-   Competitive Coding Algorithms and Data Structures
-   Security Algorithms
-   Machine Learning Algorithms
-   Statistical / Mathematical Algorithms

##  General

The summary file is used by mdBook to know what chapters to include, in what order they should appear, what their hierarchy is and where the source files are. Without this file, there is no book.

Even though  `SUMMARY.md`  is a markdown file, the formatting is very strict to allow for easy parsing. 
Let's look at how to edit `SUMMARY.md`.


```markdown
# Summary

- [Introduction](./introduction.md)
```
 Now you want to add a topic `Topic 1`. And it will have some subtopics `Sub-Topic1` and `Sub-Topic2`. 
 
```markdown
# Summary

- [Introduction](./introduction.md)
- [Topic 1](./relative/path/to/Topic-1.md)
  - [Sub Topic 1](./relative/path/to/sub-topic1.md)
  - [Sub Topic 2](./relative/path/to/sub-topic2.md)
```

It is advised to maintain the same folder structure for the markdown files as well. 
So the `Topic-1` folders will have a structure like:

```
src
├── introduction.md
├── SUMMARY.md
└── Topic-1
    ├── Sub-Topic-1
    │   ├── sub-topic-1.md
    │   └── sub-topic-2.md
    └── Topic-1.md
```

Also you need to follow proper markdown syntax for your contribution to be considered.  You can refer to this [guide](https://www.markdownguide.org/basic-syntax/).


# Contribution Guidelines

Please refer [here](./CONTRIBUTING.md) for our contributing guidelines.

# Contributors
