## 0.4.0

 * Fix: `getAttribute` now returns `null` for attributes that are not present, as per DOM4 (but in contradiction to DOM1 through DOM3).
 * Fix: static `NodeList`-returning methods (such as `querySelectorAll`) now return a real `NodeList` instance.
 * Change: `NodeList`s no longer expose nonstandard properties to the world, like `toArray`, without first prefixing them with an underscore.
 * Change: `NodeList`s no longer inconsistently have array methods. Previously, live node lists would have `indexOf`, while static node lists would have them all. Now, they have no array methods at all, as is correct per the specification.

## 0.3.4

 * Fix: stylesheets with `@media` rules were crashing calls to `getComputedStyle`, e.g. those in jQuery's initialization.

## 0.3.3

 * Fix: make `document.write` calls insert new elements correctly. (johanoverip, kblomquist).
 * Fix: `<input>` tags with no `type` attribute now return a default value of `"text"` when calling `inputEl.getAttribute("type")`.

## 0.3.2

 * Fix: stylesheets with "joining" rules (i.e. those containing comma-separated selectors) now apply when using `getComputedStyle`. (chad3814, godmar)
 * Add: support for running the tests using @aredridel's [html5](https://npmjs.org/package/html5) parser, as a prelude toward maybe eventually making this the default and fixing various parsing bugs.

## 0.3.1 (hotfix)

 * Fix: crashes when invalid selectors were present in stylesheets.

## 0.3.0

 * Fix: a real `querySelector` implementation, courtesy of the nwmatcher project, solves many outstanding `querySelector` bugs.
 * Add: `matchesSelector`, again via nwmatcher.
 * Add: support for styles coming from `<style>` and `<link rel="stylesheet">` elements being applied to the results of `window.getComputedStyle`. (chad3814)
 * Add: basic implementation of `focus()` and `blur()` methods on appropriate elements. More work remains.
 * Fix: script filenames containing spaces will now work when passed to `jsdom.env`. (TomNomNom)
 * Fix: elements with IDs `toString`, `hasOwnProperty`, etc. could cause lots of problems.
 * Change: A window's `load` event always fires asynchronously now, even if no external resources are necessary.
 * Change: turning off mutation events is not supported, since doing so breaks external-resource fetching.

## 0.2.19

 * Fix: URL resolution was broken on pages that included `href`-less `<base>` tags.
 * Fix: avoid putting `attr` in the global scope when using node-canvas. (starsquare)
 * Add: New `SkipExternalResources` feature accepts a regular expression. (fgalassi)

## 0.2.18

 * Un-revert: cssstyle has fixed its memory problems, so we get back accurate `cssText` and `style` properties again.

## 0.2.17 (hotfix)

 * Revert: had to revert the use of the cssstyle package. `cssText` and `style` properties are no longer as accurate.
 * Fix: cssstyle was causing out-of-memory errors on some larger real-world pages, e.g. reddit.com.

## 0.2.16
 * Update: Sizzle version updated to circa September 2012.
 * Fix: when setting a text node's value to a falsy value, convert it to a string instead of coercing it to `""`.
 * Fix: Use the cssstyle package for `CSSStyleDeclaration`, giving much more accurate `cssText` and `style` properties on all elements. (chad3814)
 * Fix: the `checked` property on checkboxes and radiobuttons now reflects the attribute correctly.
 * Fix: `HTMLOptionElement`'s `text` property should return the option's text, not its value.
 * Fix: make the `name` property only exist on certain specific tags, and accurately reflect the corresponding `name` attribute.
 * Fix: don't format `outerHTML` (especially important for `<pre>` elements).
 * Fix: remove the `value` property from `Text` instances (e.g. text nodes).
 * Fix: don't break in the presence of a `String.prototype.normalize` method, like that of sugar.js.
 * Fix: include level3/xpath correctly.
 * Fix: many more tests passing, especially related to file:/// URLs on Windows. Tests can now be run with `npm test`.

## 0.2.15
 * Fix: make sure that doctypes don't get set as the documentElement (Aria Stewart)
 * Add: HTTP proxy support for jsdom.env (Eugene Ware)
 * Add: .hostname and .pathname properties to Anchor elements to comply with WHATWG standard (Avi Deitcher)
 * Fix: Only decode HTML entities in text when not inside a `<script>` or `<style>` tag. (Andreas Lind Petersen)
 * Fix: HTMLSelectElement single selection implemented its type incorrectly as 'select' instead of 'select-one' (John Roberts)

## 0.2.14
 * Fix: when serializing single tags use ' />' instead of '/>' (kapouer)
 * Fix: support for contextify simulation using vm.runInContext (trodrigues)
 * Fix: allow jsdom.env's config.html to handle file paths which contain spaces (shinuza)
 * Fix: Isolate QuerySelector from prototype (Nao Iizuka)
 * Add: setting textContent to '' or clears children (Jason Davies)
 * Fix: jsdom.env swallows exceptions that occur in the callback (Xavi)

## 0.2.13
 * Fix: remove unused style property which was causing explosions in 0.2.12 and node 0.4.7

## 0.2.12
 * Fix: do not include gmon.out/v8.log/tests in npm distribution

## 0.2.11
 * Add: allow non-unique element ids (Avi Deitcher)
 * Fix: make contexify an optional dependency (Isaac Schlueter)
 * Add: scripts injected by jsdom are now marked with a 'jsdom' class for serialization's sake (Peter Lyons)
 * Fix: definition for ldquo entity (Andrew Morton)
 * Fix: access NamedNodeMap items via property (Brian McDaniel)
 * Add: upgrade sizzle from 1.0 to [fe2f6181](https://github.com/jquery/sizzle/commit/fe2f618106bb76857b229113d6d11653707d0b22) which is roughly 1.5.1
 * Add: documentation now includes `jsdom.level(x, 'feature')`
 * Fix: make `toArray` and `item` on `NodeList` objects non-enumerable properties
 * Add: a reference to `window.close` in the readme
 * Fix: Major performance boost (Felix Gnass)
 * Fix: Using querySelector `:not()` throws a `ReferenceError` (Felix Gnass)

## 0.2.10
 * Fix: problems with lax dependency versions
 * Fix: CSSOM constructors are hung off of the dom (Brian McDaniel)
 * Fix: move away from deprecated 'sys' module
 * Fix: attribute event handlers on bubbling path aren't called (Brian McDaniel)
 * Fix: setting textarea.value to markup should not be parsed (Andreas Lind Petersen)
 * Fix: content of script tags should not be escaped (Ken Sternberg)
 * Fix: DocumentFeatures for iframes with no src attribute. (Brian McDaniel) Closes #355
 * Fix: 'trigger' to 'raise' to be a bit more descriptive
 * Fix: When `ProcessExternalResources['script']` is disabled, do _not_ run inline event handlers. #355
 * Add: verbose flag to test runner (to show tests as they are running and finishing)

## 0.2.9
 * Fix: ensure features are properly reset after a jsdom.env invocation. Closes #239
 * Fix: ReferenceError in the scanForImportRules helper function
 * Fix: bug in appendHtmlToElement with HTML5 parser (Brian McDaniel)
 * Add: jsonp support (lheiskan)
 * Fix: for setting script element's text property (Brian McDaniel)
 * Fix: for jsdom.env src bug
 * Add: test for jsdom.env src bug (multiple done calls)
 * Fix: NodeList properties should enumerate like arrays (Felix Gnass)
 * Fix: when downloading a file, include the url.search in file path
 * Add: test for making a jsonp request with jquery from jsdom window
 * Add: test case for issue #338
 * Fix: double load behavior when mixing jsdom.env's `scripts` and `src` properties (cjroebuck)

## 0.2.8 (hotfix)
 * Fix: inline event handlers are ignored by everything except for the javascript context

## 0.2.7 (hotfix)
 * Fix stylesheet loading

## 0.2.6
 * Add: support for window.location.search and document.cookie (Derek Lindahl)
 * Add: jsdom.env now has a document configuation option which allows users to change the referer of the document (Derek Lindahl)
 * Fix: allow users to use different jsdom levels in the same process (sinegar)
 * Fix: removeAttributeNS no longer has a return value (Jason Davies)
 * Add: support for encoding/decoding all html entities from html4/5 (papandreou)
 * Add: jsdom.env() accepts the same features object seen in jsdom.jsdom and friends

## 0.2.5
 * Fix: serialize special characters in Element.innerHTML/Element.attributes like a grade A browser (Jason Priestley)
 * Fix: ensure Element.getElementById only returns elements that are attached to the document
 * Fix: ensure an Element's id is updated when changing the nodeValue of the 'id' attribute (Felix Gnass)
 * Add: stacktrace to error reporter (Josh Marshall)
 * Fix: events now bubble up to the window (Jason Davies)
 * Add: initial window.location.hash support (Josh Marshall)
 * Add: Node#insertBefore should do nothing when both params are the same node (Jason Davies)
 * Add: fixes for DOMAttrModified mutation events (Felix Gnass)

## 0.2.4
 * Fix: adding script to invalid/incomplete dom (document.documentElement) now catches the error and passes it in the `.env` callback (Gregory Tomlinson)
 * Cleanup: trigger and html tests
 * Add: support for inline event handlers (ie: `<div onclick='some.horrible.string()'>`) (Brian McDaniel)
 * Fix: script loading over https (Brian McDaniel) #280
 * Add: using style.setProperty updates the style attribute (Jimmy Mabey).
 * Add: invalid markup is reported as an error and attached to the associated element and document
 * Fix: crash when setChild() failes to create new DOM element (John Hurliman)
 * Added test for issue #287.
 * Added support for inline event handlers.
 * Moved frame tests to test/window/frame.js and cleaned up formatting.
 * Moved script execution tests to test/window/script.js.
 * Fix a crash when setChild() fails to create a new DOM element
 * Override CSSOM to update style attribute

## 0.2.3
 * Fix: segfault due to window being garbage collected prematurely
    NOTE: you must manually close the window to free memory (window.close())

## 0.2.2
 * Switch to Contextify to manage the window's script execution.
 * Fix: allow nodelists to have a length of 0 and toArray to return an empty array
 * Fix: style serialization; issues #230 and #259
 * Fix: Incomplete DOCTYPE causes JavaScript error
 * Fix: indentation, removed outdated debug code and trailing whitespace.
 * Prevent JavaScript error when parsing incomplete `<!DOCTYPE>`. Closes #259.
 * Adding a test from brianmcd that ensures that setTimeout callbacks execute in the context of the window
 * Fixes issue 250: make `document.parentWindow === window` work
 * Added test to ensure that timer callbacks execute in the window context.
 * Fixes 2 issues in ResourceQueue
 * Make frame/iframe load/process scripts if the parent has the features enabled

## 0.2.1
 * Javascript execution fixes [#248, #163, #179]
 * XPath (Yonathan and Daniel Cassidy)
 * Start of cssom integration (Yonathan)
 * Conversion of tests to nodeunit! (Martin Davis)
 * Added sizzle tests, only failing 3/15
 * Set the title node's textContent rather than its innerHTML #242.  (Andreas Lind Petersen)
 * The textContent getter now walks the DOM and extract the text properly. (Andreas Lind Petersen)
 * Empty scripts won't cause jsdom.env to hang #172 (Karuna Sagar)
 * Every document has either a body or a frameset #82. (Karuna Sagar)
 * Added the ability to grab a level by string + feature. ie: jsdom.level(2, 'html') (Aria Stewart)
 * Cleaned up htmlencoding and fixed character (de)entification #147, #177 (Andreas Lind Petersen)
 * htmlencoding.HTMLDecode: Fixed decoding of `&lt;`, `&gt;`, `&amp;`, and `&apos;`. Closes #147 and #177.
 * Require dom level as a string or object. (Aria Stewart)
 * JS errors ar triggered on the script element, not document. (Yonathan)
 * Added configuration property 'headers' for HTTP request headers. (antonj)
 * Attr.specified is readonly - Karuna Sagar
 * Removed return value from setAttributeNS() #207 (Karuna Sagar)
 * Pass the correct script filename to runInContext. (robin)
 * Add http referrer support for the download() function. (Robin)
 * First attempt at fixing the horrible memory leak via window.stopTimers() (d-ash)
 * Use vm instead of evals binding (d-ash)
 * Add a way to set the encoding of the jsdom.env html request.
 * Fixed various typos/lint problems (d-ash)
 * The first parameter download is now the object returned by URL.parse(). (Robin)
 * Fixed serialization of elements with a style attribute.
 * Added src config option to jsdom.env() (Jerry Sievert)
 * Removed dead code from getNamedItemNS() (Karuna Sagar)
 * Changes to language/javascript so jsdom would work on v0.5.0-pre (Gord Tanner)
 * Correct spelling of "Hierarchy request error" (Daniel Cassidy)
 * Node and Exception type constants are available in all levels. (Daniel Cassidy)
 * Use \n instead of \r\n during serialization
 * Fixed auto-insertion of body/html tags  (Adrian Makowski)
 * Adopt unowned nodes when added to the tree. (Aria Stewart)
 * Fix the selected and defaultSelected fields of `option` element. - Yonathan
 * Fix: EventTarget.getListeners() now returns a shallow copy so that listeners can be safely removed while an event is being dispatched. (Felix Gnass)
 * Added removeEventListener() to DOMWindow (Felix Gnass)
 * Added the ability to pre-load scripts for jsdom.env() (Jerry Sievert)
 * Mutation event tests/fixes (Felix Gnass)
 * Changed HTML serialization code to (optionally) pretty print while traversing the tree instead of doing a regexp-based postprocessing. (Andreas Lind Petersen)
 * Relative and absolute urls now work as expected
 * setNamedItem no longer sets Node.parentNode #153 (Karuna Sagar)
 * Added missing semicolon after entity name - Felix Gnass
 * Added NodeList#indexOf implementation/tests (Karuna Sagar)
 * resourceLoader.download now works correctly with https and redirects (waslogic)
 * Scheme-less URLs default to the current protocol #87 (Alexander Flatter)
 * Simplification the prevSibling(), appendChild(), insertBefore() and replaceChild() code (Karuna Sagar)
 * Javascript errors use core.Node.trigger (Alexander Flatter)
 * Add core.Document.trigger in level1/core and level2/events; Make DOMWindow.console use it (Alexander Flatter)
 * Resource resolver fixes (Alexander Flatter)
 * Fix serialization of doctypes with new lines #148 (Karuna Sagar)
 * Child nodes are calculated immediately instead of after .length is called #169, #171, #176 (Karuna Sagar)
