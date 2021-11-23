# Document Annotation

**Document Annotation** is a tool for annotating multi-page documents,
built with [React](https://reactjs.org/) and [Redux](https://redux.js.org/)
(front-end) and [Express](http://expressjs.com/) (back-end).

Annotations are defined in a JSON format for the entire document.
Annotations are descriptive and are arranged in order in a hierarchical tree
structure (similar to markup languages like TeX and HTML). Leaves of the tree
constitute bounding boxes referenced to individual pages.

## Getting Started

The project consists of a client (*doc-anno-client*) and a server
(*doc-anno-server*). The client offers a web interface for viewing and editing
document annotations. It communicates with the server which hosts the documents
(including PDFs, thumbnail PNGs and annotation JSONs).

Note that to deploy the application, you only need to run the server.
When the client is built, a set of static files appear in its *build* directory.
The server hosts both client and server by passing through any requests
which don't address static files or its API to the client.

### Prerequisites

- [Node.js](https://nodejs.org/)
- [Yarn](https://yarnpkg.com/)
- [Python 3](https://www.python.org/)
  - [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) (`bs4`)
  - [lxml](https://lxml.de/) (`lxml`)
  - [pdfminer](https://github.com/pdfminer/pdfminer.six)(`pdfminer`)
- [ImageMagick](https://www.imagemagick.org/)
  - Security policy domain `coder` rights `read|write` for pattern `PDF`
  - Security policy domain `coder` rights `read|write` for pattern `LABEL`
  - In file `/etc/ImageMagick-6/policy.xml` (or `/etc/ImageMagick/policy.xml`):
  ```
  <policy domain="coder" rights="read|write" pattern="PDF" />
  <policy domain="coder" rights="read|write" pattern="LABEL" />
  ```

### Pre-Installation
```python
pip install pdfminer.six
```


### Installation

- Client
  - `yarn install`
  - `yarn build`
- Server
  - `yarn install`
  - `yarn start`

### Development

- Client
  - `yarn install`
  - `yarn start`
- Server
  - `yarn install`
  - `PORT=3001 yarn start`

## Application Structure

Directory `public/documents/` contains all the documents, ordered by datasets.
It is structured as follows:

- **Dataset**: `demo/`
  - **Document**: `example/`
    - Document spec: `example.json`
    - PDF document: `example.pdf`
    - Page images: `example-0.png`, `example-1.png`, etc.
    - Annotations: `example-original.json`, `example-draft.json`, etc.

## Annotation Guidelines
- Rule of thumb. "Once you are in the annotator GUI, before annotating each file, make sure you do (1) new name (e.g., GTJ), (2) click ""copy"", (3) click ""store"".

Make sure you always store the intermediary annotations."

        

- Command in GUI.        awsd for +/- size  and ijkl for position shift

 

- Multiple select in the document.        "You select them via click+drag

bounding boxes can be copied by pressing 'c'

then you can unselect, move your cursor to a position you want and press 'v'

 

If you select a category in the drop-down on the top left, they pasted annotations will all be of that selected category"

 

- Add a new annotation in the tree.    "either via the (+) button next to the drop-down on the top left

or by pressing ""Add"" on a node in the tree

they'll always be added on the very bottom of the children

of the currently selected node in the tree"

