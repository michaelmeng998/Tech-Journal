# Initial Thoughts About Using Flutter

## Steps for Quickly Creating a UI:

- Often times it is better to create something simple and robust than creating something that is 'fancy'. A lot of moving parts may lead to a nice looking UI, but it has the downside of becoming too fragile (i.e. changing one or two elements may break the whole thing)
- Some general steps I have followed when beginning to build layouts:
1. Layout objects and text in `Rows` and `Columns` and set `mainAxisAlignment` and `crossAxisAlignment` in both
2. Set your styles using `Padding`, `Align` or `Extended` and so forth. `Container` is also useful (you can set decoration and margin in here)

### Some other stuff I've learned:
- You can use a `SizedBox(height: whatever)` to create spacing instead of using `Padding`
- Looking at the UI from the top-down or from left to right? I'm still learning but perhaps defining elements from the top down and putting an `Expanded` at the bottom is a good initial approach? This will help avoid problems with overflow elements and also help avoid declaring a lot of absolute values. (i.e. using `Expanded` within a `Column` or `Row`)

### Using Keys:
- [Cool 9 minute video explaining usage of keys](https://www.youtube.com/watch?v=kn0EOS-ZiIc)
- Keys can be used when re-ordering elements of similar type that have state (ex. in lists)
- Understanding the Widget Tree and Element Tree:
1. When updating, the Element Tree is walked and is checked in reference to the Widget Tree
2. It checks if it is the same type and key as the Widget and will update the reference accordingly. 
3. However, imagine if there is a stateful widget without a key bound to it. When the element tree is walked, then the elements and widgets appear to be of the same type and nothing is changed. It ignores the state attached to the element. 
4. If we add a key, Flutter recognizes the inconsistency and de-activates the element and searches for the appropriate key that matches with the corresponding state. 
- There is also additional issues with hierarchy. The Flutter widget and element matching system looks at one level of the tree at a time. It only matches keys within a particular level, and if it can't find it it will create a new element and initializes a new state. 

- use a `ValueKey` when you have a unique identifier for each widget
- use a `ObjectKey` when you have an array of identifiers for a widget
- use a `UniqueKey` when you don't have any unique identifiers attached
- `PageStorageeKeys` preserve scroll location
- `GlobalKey`: they allow widgets to change parents anywhere in your app without losing state, or they can be used to access information about another widget in a completely different part of the widget tree.

### Useful Guides:
- https://flutter.dev/docs/development/ui/layout
- https://medium.com/@liewjuntung/tips-on-using-android-studio-to-develop-flutter-apps-9e42c047b7f4
- https://hackernoon.com/practical-flutter-my-personal-6-tips-for-newcomers-dfbe44a29246

### Text Align in Flutter:
- https://stackoverflow.com/questions/51638176/under-which-circumstances-textalign-property-works-in-flutter

