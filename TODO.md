# Initial requirements

We should provide the core functionality already duplicated across the various
CEM projects in the wild.

## Existing utilities

### CEM analyzer

- `getAllExportsOfKind`
  - Filters the exports by a particular `kind`
- `getAllDeclarationsOfKind`
  - Filters the declarations by a particular `kind`
- `getInheritanceTree`
  - Gets the inheritance hierarchy of a given class name, as an array of
class names
- `getModuleFromManifests`
  - Finds a particular module by `path` in a set of manifests
- `getModuleForClassLike`
  - Finds a particular module's path which contains a class or mixin with the
specified name
- `getClassMemberDoc`
  - Finds a class by name within a given module, then finds a member by name
within that class.

### CE language server

- `findClassForTagName`
  - Finds the class from a set of manifests which has the specified tag name
associated with it
- `findCustomElementDeclarationFromModule`
  - Finds the first custom element class declared in a given module
- `findDeclarationForTagName`
  - Finds the custom element declaration from a set of manifests which
has the specified tag name associated with it
- `findCustomElementTagLike`
  - Finds a registered tag which contains the specified string
- `getCustomElementTags`
  - Finds all the registered tags from a set of manifests
- `findCustomElementDefinitionModule`
  - Finds the module from a set of manifests which registered a given tag name
- `findTagNameForClass`
  - Finds the tag name associated with the specified class name from a set of
manifests
- `moduleHasCustomElementExport`
  - Determines if a module exports a custom element
- `exportHasCustomElementExport`
  - Determines if an export is a custom element export
- `moduleHasCustomElementExportByName`
  - Determines if a module exports the specified tag name
- `exportHascustomElementExportByName`
  - Determines if an export is a custom element definition with a particular
name
- `findModuleByPath`
  - Finds a module from a set of manifests which has the specified `path`
- `modulePathEquals`
  - Determines if a module's path matches a given path
- `isCustomElementDeclaration`
  - Determines if a declaration is a custom element declaration

### webcomponents.org

- `getCustomElements`
  - Finds all custom elements exported by a given package, returning their
export and declaration amongst other things
- `getModule`
  - Finds the module in a given package which has a path matching the one
specified
- `isClassDeclaration`
  - Determines if a declaration is a class declaration
- `isFunctionDeclaration`
  - Determines if a declaration is a function declaration
- `isMixinDeclaration`
  - Determines if a declaration is a mixin declaration
- `isVariableDeclaration`
  - Determines if a declaration is a variable declaration
- `isCustomElement`
  - Determines if a declaration is a custom element declaration or a
custom element mixin declaration
- `isCustomElementDeclaration`
  - Determines if a declaration is a custom element declaration
- `isCustomElementMixinDeclaration`
  - Determines if a declaration is a custom element mixin declaration
- `resolveReference`
  - Resolves a `Reference` to an actual `Module` from a set of manifests

## Proposed API

TBD

Roughly it seems we need a few areas of utilities:

- Type guards (e.g. `isClassDeclaration`)
- Traversal functions (various `find`-like functions mostly)
- Assertion functions (e.g. `exportHasCustomElementExport`)
- Getters (e.g. `getAllExportsOfKind`)

The getters could actually end up being `findAll`-like functions, i.e. the
multiple version of the traversal functions.

In that case we would have `findX` and `findAllX` or similar.
