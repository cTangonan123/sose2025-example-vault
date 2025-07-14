---
tags:
  - cs
  - csonline
  - csumb
  - cti
  - accelerate
  - excalidraw
  - test-case-studies
repo: https://www.github.com/excalidraw/excalidraw
primary-issue: "9606"
---
# Case Studies Related to your Issue
## Resources
-  [GitHub Docs: Searching issues and pull requests](https://docs.github.com/en/search-github/searching-on-github/searching-issues-and-pull-requests#search-by-qualifier)
- [[Finding Case Studies–Use This|table generated through copilot]]
- [f] [Example for searching](https://github.com/excalidraw/excalidraw/pulls)

## 🤖 Prompting with Copilot
- ["] "Could you generate me a markdown table with the headings: $X$, $Y$, $Z$"
	- let $X$, $Y$, $Z$  be relevant headings you want
	- just copy and paste, and use the table to add or drop rows columns as needed.

## 🔍 Search Queries
- 🔍 is:pr is:closed in:title "$X$"
	- let $X$ be some relevant piece related to your issue
	- [>] sort descending to find original implementation of $X$
- 🔍 is:pr is:closed author:$Y$
	- let $Y$ be some maintainer of the repo

---
# Case Studies Examples: using Issue #9606
keywords searched: `double-click` `group` `align` `distribute`
- use [[Finding Case Studies–Use This|Github search bar helper]]

This is to evaluate PR's in relation to issue #9606
- List of Possible Issues
- [[Finding Case Studies–Use This]]

| link to issue                                                                                   | link to PR                                                  | Relevance Scale (⭐️⭐️⭐️⭐️⭐️) | Why?                                                                                     | Why Not?                                           |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------- | ---------------------------------------------------------------------------------------- | -------------------------------------------------- |
| [#173 Group Elements](https://github.com/excalidraw/excalidraw/issues/173)                      |                                                             | ⭐️⭐️⭐️⭐️☆                    | First issue posed in writing                                                             | no relevant pull request, was closed without merge |
| [#1656 groups should have atomic z-index](https://github.com/excalidraw/excalidraw/issues/1656) | [#1648](https://github.com/excalidraw/excalidraw/pull/1648) | ⭐️⭐️⭐️⭐️⭐️                   | very relevant, plenty of dialog, and commits                                             | no reason                                          |
|                                                                                                 | [#2092](https://github.com/excalidraw/excalidraw/pull/2092) | ⭐️⭐️⭐️⭐️⭐️                   | made by maintainer, all has test implementation I could refer to later                   | no reason                                          |
| [#4467](https://github.com/excalidraw/excalidraw/issues/4467)                                   | [#4468](https://github.com/excalidraw/excalidraw/pull/4468) | ⭐️⭐️⭐️⭐️⭐️                   | made by a maintainer, and incorporates the alignment tool as suggested in original issue | no issue                                           |
| [#772](https://github.com/excalidraw/excalidraw/issues/772)                                     | [#2267](https://github.com/excalidraw/excalidraw/pull/2267) | ⭐️⭐️⭐️⭐️⭐️                   | original implementation, of the `alignAction.ts`                                         | no issue                                           |
| [#1656](https://github.com/excalidraw/excalidraw/issues/1656)                                   | [#1648](https://github.com/excalidraw/excalidraw/pull/1648) | ⭐️⭐️⭐️⭐️⭐️                   | original implementation of `groups.ts`                                                   | no issue                                           |

---
## Test Case 01: Initialization of Group type

|         Category | first Initialization of type `groups`                                                         |
| ---------------: | --------------------------------------------------------------------------------------------- |
|        **Issue** | [#1656 Groups Should have atomic index](https://github.com/excalidraw/excalidraw/issues/1656) |
| **Pull Request** | [#1648](https://github.com/excalidraw/excalidraw/pull/1648)                                   |
|    **Reasoning** | First instantiation of group feature                                                          |
|  **Directories** | `src/actions` `src/components` `src/element` `tests/__snapshots__`                            |
|        **Files** | `actionGroup.tsx` `groups.ts`  `index.ts` `types.ts` `appState.ts`                            |
|            tests | `dragCreate` `move` `multiPointCreate` `resize` `selection`                                   |

### Notes
#### `src/actions/actionGroup.ts`
- provides the logic to to compose unsser interaction between canvas/interactiveCanvas and client 'actions'
- should export all methods used:
- 

`src/actions/types.ts`
- looks to add the group and ungroup AppState variable
- 

`src/actions/appState.ts`
- editingGroupId and selectedGroupIds is inculded into state

`src/groups.ts`
- file dedicated to the grouping,
- ==holds core logic for groups, Definitely something there.==

### Todos
- [x] compare across local project any changes made since to the relevant files see relevant changes to
	- Conclusion: Excalidraw recently changed to a monorepo with some of their auxillary packaging joined into their parent repo. Core logic still the same but placed elsewhere.


---
## Test Case 02: Helper method emphasis (look at methods in relation to `group.ts`)

|         Category | helper method emphasis                                                          |
| ---------------: | ------------------------------------------------------------------------------- |
|        **Issue** |                                                                                 |
| **Pull Request** | [#2092 Fix Group Selection](https://github.com/excalidraw/excalidraw/pull/2092) |
|    **Reasoning** | pull request made by maintainer                                                 |
|  **Directories** | `src/components`                                                                |
|        **Files** | `App.tsx`                                                                       |
|            tests | `regressionTests`                                                               |
### Notes
- small PR mainly focused on utilizing the accessible methods in `groups.ts`

|Helper Method Name|Description|File/Location|
|---|---|---|
|`isElementInGroup`|Checks if an element is in a specific group.|[groups.ts#L278](https://github.com/excalidraw/excalidraw/blob/master/packages/element/src/groups.ts#L278)|
|`getElementsInGroup`|Returns all elements in the specified group.|[groups.ts#L282](https://github.com/excalidraw/excalidraw/blob/master/packages/element/src/groups.ts#L282)|
|`getSelectedGroupIdForElement`|Finds the selected group ID for a given element, given the selected group IDs.|[groups.ts#L294](https://github.com/excalidraw/excalidraw/blob/master/packages/element/src/groups.ts#L294)|
|`addToGroup`|Adds a new group ID to an element's group IDs.|[groups.ts#L300](https://github.com/excalidraw/excalidraw/blob/master/packages/element/src/groups.ts#L300)|
|`selectGroupsForSelectedElements`|Selects all relevant group IDs and editing group IDs for the currently selected elements.|[groups.ts#L165](https://github.com/excalidraw/excalidraw/blob/master/packages/element/src/groups.ts#L165)|
|`getNonDeletedGroupIds`|Gets all non-deleted group IDs from all elements.|[groups.ts#L349](https://github.com/excalidraw/excalidraw/blob/master/packages/element/src/groups.ts#L349)|
|`elementsAreInSameGroup`|Checks if all provided elements are in the same group.|[groups.ts#L369](https://github.com/excalidraw/excalidraw/blob/master/packages/element/src/groups.ts#L369)|



---
## Test Case 03: Clean up of align group and distribute

|         Category | clean up of align group and distribute                                                                                     |
| ---------------: | -------------------------------------------------------------------------------------------------------------------------- |
|        **Issue** | [#4467](https://github.com/excalidraw/excalidraw/issues/4467)                                                              |
| **Pull Request** | [#4468 fix: align and distribute binded text in container and cleanup](https://github.com/excalidraw/excalidraw/pull/4468) |
|    **Reasoning** | pull request made by maintainer                                                                                            |
|  **Directories** | `src/element` `src`                                                                                                        |
|        **Files** | `bounds.ts` `/groups.ts` `src/distribute.ts` `src/align.ts`                                                                |
|            tests | `regressionTests`                                                                                                          |

### Notes
- small cleanup and refactoring, ideally learned that `bound.ts` will also be an added file that I can utilize for possible implementation of group alignment

---
## Test Case 04: Implementation of Align tool

|         Category | Implementation of the Align tool                                                                                                    |
| ---------------: | ----------------------------------------------------------------------------------------------------------------------------------- |
|        **Issue** | [#772 Feature Request](https://github.com/excalidraw/excalidraw/issues/772)                                                         |
| **Pull Request** | [Feature: Align Elements#2267](https://github.com/excalidraw/excalidraw/pull/2267)                                                  |
|    **Reasoning** | pull request of original implementation of the action `align`, (`distribute?`)                                                      |
|  **Directories** | `src/actions` `src/components` ~~`src/locales?`~~ `src/tests`                                                                       |
|        **Files** | `actionAlign.tsx` `../actions/index.ts` `../components/Actions.tsx` `../components/ShortcutsDialog.tsx?` `../components/icons.tsx?` |
|            paths |                                                                                                                                     |
|            tests | `../tests/align.test.tsx`                                                                                                           |

### Notes:
- This test case evaluates the implemntation of the featured action Align
	- will do one more on distribute but I think it will be of similar type

#### `src/actions/actionAlign.tsx`
```typescript title:@line(21-24) info:4
const enableActionGroup = (
	elements: readonly ExcalidrawElement[],
	appState:AppState,
) => getSelectedElements(getNonDeletedElements(elements), appState).length >1;
```
- so you must first enable an action with a boolean value
- ActionGroup is different than selecting an elements in a group
	- group has multiple meanings in this codebase it seems.
	- ==could technically be at this point where the condition must also account for when in a selected group state==
- will also have to check when:
	- user has a group, double-clicks, does `getNonDeletedElements(elements)` return the elements in the app?
- looks as if the methods for various alignments i.e.: `actionAlignTop` `actionAlignBottom` etc... ~~are of type: `Alignment`, inherently.~~
	- of these methods `register()` is called, so it registers an action, determining what condition
- this holds the react logic for translating the alignment action

#### `src/actions/index.ts`
- index is where the methods are exported most likely imported in the main `App.ts`

#### `src/actions/types.ts`
- this is where types are defined

#### `src/align.ts`
- the Type for Alignment holds a `position` and `axis` value

```typescript title:"@line(12-14) Alignment Type" 
export interface Alignment {
  position: "start" | "center" | "end";
  axis: "x" | "y";
}
```

- ==will have to look into groups to determine if "group" has a different semantic meaning the the group I am interested in.==
```typescript title:"@line(40-57) getMaximumGroups()"
export const getMaximumGroups = (
  elements: ExcalidrawElement[],
): ExcalidrawElement[][] => {
  const groups: Map<String, ExcalidrawElement[]> = new Map<
    String,
    ExcalidrawElement[]
  >();

  elements.forEach((element: ExcalidrawElement) => {
    const groupId =
      element.groupIds.length === 0
        ? element.id
        : element.groupIds[element.groupIds.length - 1];

    const currentGroupMembers = groups.get(groupId) || [];

    groups.set(groupId, [...currentGroupMembers, element]);
  });

  return Array.from(groups.values());
};
```

- `calculateTranslation()` seems to be the core logic for elements that qualify, probably not of interest,

#### `src/tests/align.test.tsx`
- simple structure, most likely will reference this again as we will need to generate tests in this file
- just follow the same format



## Base line assumptions
- So it seems the project structure changed recently, files are all still there but their location may be diffferent, probably best to ensure that we are in the `packages/excalidraw` folder, as most of it is the source code for the repository.

### ~~`actionAlign.tsx`~~
- [p] predicate may not be where the issue lies although could optionally check whether or not

- relevant AppState?.properties:
- `editingGroupId`: default set to null,
	- predicate could have an additional condition for align such as:
	- ==...appState.editingGroupId != null && selectedElements.length > 1==
	- below could be all that is required ⬇️ in `../actionAlign.tsx`

```tsx title:"packages/excalidraw/actions/actionAlign.tsx" info:9
export const alignActionsPredicate = (
	appState: UIAppState,
	app: AppClassProperties,
) => {
	const selectedElements = app.scene.getSelectedElements(appState);
	return (
		selectedElements.length > 1 &&
		// TODO enable aligning frames when implemented properly
		(!selectedElements.some((el) => isFrameLikeElement(el)) || appState.editingGroupId !== null)
	);
};
```

We could probably test the same in regards to `../actionDistribute.tsx` too

```tsx title:"../actionDistribute.tsx"
const enableActionGroup = (appState: AppState, app: AppClassProperties) => {
  const selectedElements = app.scene.getSelectedElements(appState);
  return (
    selectedElements.length > 1 &&
    // TODO enable distributing frames when implemented properly
    (!selectedElements.some((el) => isFrameLikeElement(el)) || appState.editingGroupId !== null)
  );
};

```

