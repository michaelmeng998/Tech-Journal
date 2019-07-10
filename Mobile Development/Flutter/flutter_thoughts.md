# Initial Thoughts About Using Flutter

## Steps for Quickly Creating a UI:

- Often times it is better to create something simple and robust than creating something that is 'fancy'. A lot of moving parts may lead to a nice looking UI, but it has the downside of becoming too fragile (i.e. changing one or two elements may break the whole thing)
- Some general steps I have followed when beginning to build layouts:
1. Layout objects and text in `Rows` and `Columns` and set `mainAxisAlignment` and `crossAxisAlignment` in both
2. Set your styles using `Padding`, `Align` or `Extended` and so forth. `Container` is also useful (you can set decoration and margin in here)

### Some other stuff I've learned:
- You can use a `SizedBox(height: whatever)` to create spacing instead of using `Padding`
- Looking at the UI from the top-down or from left to right? I'm still learning but perhaps defining elements from the top down and putting an `Expanded` at the bottom is a good initial approach? This will help avoid problems with overflow elements and also help avoid declaring a lot of absolute values. (i.e. using `Expanded` within a `Column` or `Row`)

### Useful Guides:
- https://flutter.dev/docs/development/ui/layout
- https://medium.com/@liewjuntung/tips-on-using-android-studio-to-develop-flutter-apps-9e42c047b7f4
- https://hackernoon.com/practical-flutter-my-personal-6-tips-for-newcomers-dfbe44a29246

### Text Align in Flutter:
- https://stackoverflow.com/questions/51638176/under-which-circumstances-textalign-property-works-in-flutter

