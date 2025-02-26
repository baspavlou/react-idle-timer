# Changelog

## 5.0.0

> Version 5 is a complete, from scratch, typescript rewrite.  A lot of effort went
> into this release.  If you find this package useful and have the means, please 
> consider a small [donation]('https://github.com/sponsors/supremetechnopriest')!

#### ⚡️ Features
- Add built in prompt handling.
- Add `immediateEvents` property.
- Add cross tab custom message broadcasting.
- New higher order component `withIdleTimer`.
- New provider `IdleTimerProvider`.

#### ✨ Enhancements
- Timeouts and Intervals are now hoisted into a web worker to bypass browser background throttles.
- Rewrite `crossTab` from the ground up. The new implementation is much smaller and more efficient.
- Cross Tab options simplified.
- All callbacks and methods are now memoized.

#### 🐞 Bug Fixes
- All property values can now be dynamically updated.
- Fix `getTotalActiveTime` returning negative value.
- Fix sending message on closed channel error.

#### 🔥 Code Removal
- Remove `capture` property.
- Remove `passive` property.

#### 📝 Documentation
- New documentation site.
- Add contribution guide.
- Add issue and pull request templates.

#### ⬆️ Update Dependencies
- Updated for React 17.
- Updated all dependencies.

### 4.6.4

#### 🐞 Bug Fixes
- Make `ref` optional in typedef.

### 4.6.3

#### ✨ Enhancements
- Export a bundle for modern browsers.

#### 🐞 Bug Fixes
- Add missing `ref` to TypeScript definitions.
- Fix a bug where reset would not propagate cross tab.

### 4.6.2

#### ✨ Enhancements
- Allow for dynamically setting `onActive` and `onIdle` event handlers in conjunction with cross tab event reconciliation.

### 4.6.1

#### ✨ Enhancements
- When `emitOnAllTabs` is set to `true`, `start`, `reset`, `pause` and `resume` will be called on all tabs.
- Calling `reset` will now automatically fire `onActive` while calling `start` will not. Otherwise these two methods are functionally equivalent.

#### 🐞 Bug Fixes
- Fix an issue where the `localStorage` method would not call `idle` if there wasn't any user activity on the page.
- Fix an issue where the `TabManager` would not deregister itself when the tab was closed if it was not the leader tab.

#### 🚿 Clean up
- Fix a type-o in propTypes, typescript definitions and docs.

## 4.6.0

#### ⚡️ Features
- Add cross tab support. See examples and README for usage and documentation.
- Add an `isLeader()` method that returns a boolean indicating wether or not the current tab is the lead orchestrator for cross tab reconciliation. 
- Add a `startManually` configuration option to enable starting of the timer and activity detection manually. An alias to `reset()` called `start()` is also exposed to keep the code more semantic. If `startManually` is set to `true`, the `IdleTimer` component and `useIdleTimer` hook wont start until `reset()` or `start()` are called.

#### 🐞 Bug Fixes
- Fix a bug where throttle and debounce wouldn't work at higher values in useIdleTimer.

### 4.5.6

#### 🐞 Bug Fixes
- Calling `resume` or `pause` from inside a `useEffect` will now properly bind and unbind events.

### 4.5.5

#### ✨ Enhancements
- Setting a timeout dynamically will now call `onActive` if the user is idle.

### 4.5.4

#### ✨ Enhancements
- Bind `getLastIdleTime` to component scope making the method callable.

### 4.5.3

#### ✨ Enhancements
- Bind `getTotalActiveTime` and `getTotalIdleTime` to component scope making the methods callable.

### 4.5.2

#### ✨ Enhancements
- Add the ability to set timeout after the component has been mounted. Doing so will reset the timer automatically.

### 4.5.1

#### ✨ Enhancements
- Add the ability to set timeout after the hook has been mounted. Doing so will reset the timer automatically.

## 4.5.0

#### ⚡️ Features
- Add  `getLastIdleTime` and `getTotalIdleTime` methods.

#### ✨ Enhancements
- Refactor `getTotalActiveTime` to be accurate in more scenarios.

#### 💚 CI
- Switch from travis to github actions.

### 4.4.2

#### ⬆️ Update Dependencies
- Update peerDependencies to support React versions greater than 16.

### 4.4.1

#### ⏱ Performance
- Reduce bundle size by excluding examples from npm package.

#### 📝 Documentation
- Update README.md.

## 4.4.0

#### ⚡️ Features
- Add `getTotalActiveTime` method.  Returns the total time in milliseconds the user was active.

### 4.3.7

#### ✨ Enhancements
- Add more event types to typescript definition

#### 📝 Documentation
- Fix a type-o in the default events (mouseWheel -> mousewheel)

### 4.3.6

#### 📝 Documentation
- Fix a type-o in the README examples.

### 4.3.5

#### 🐞 Bug Fixes
- Fix a regression affecting older minifiers that don't know how to deal with `let` and `const`. Re-implement babel to transpile to `var`.

### 4.3.4

#### 🐞 Bug Fixes
- Fix a regression where `debounce` and `throttle` were not applied to `onAction`.

### 4.3.2

#### 🐞 Bug Fixes
- Fix an issue where callback functions were not being updated. #122

### 4.3.1

#### 🐞 Bug Fixes
- Fix an issue with TypeScript typings.

#### 📝 Documentation
- Add TypeScript examples.

## 4.3.0

#### ⚡️ Features
- Add `useIdleTimer` hook implementation.
- Add `eventsThrottle` to reduce cpu using on events that can spam the event handler. Defaults to 200ms.

#### ⬆️ Update Dependencies
- Update all dependencies, added new examples and cleaned up build chain.

### 4.2.12

#### ✨ Enhancements
- Add `visibilitychange` event to default events. #98

### 4.2.11

#### 🐞 Bug Fixes
- Fix an issue with mobile devices when the browser is backgrounded with `stopOnIdle` set. #96

### 4.2.10

#### 🐞 Bug Fixes
- Fix a bug where onIdle was not triggered consistently on iOS. #94
- Refactor of toggleIdle function to prevent race conditions. #93

### 4.2.9

#### 🐞 Bug Fixes
- Fix a bug where HMR systems would prevent events from unbinding. #87

### 4.2.8

#### 🐞 Bug Fixes
- Fix a bug where a paused timer would return the wrong remaining time when resumed.

### 4.2.7

#### 🐞 Bug Fixes
- Fixes a regression introduced in v4.2.6 affecting `getRemainingTime()`.

### 4.2.6

#### 🐞 Bug Fixes
- Fix a bug where `reset()` was not resetting `getRemainingTime()`.
- `componentWillMount` is deprecated. Moved logic to `componentDidMount`.

#### ⬆️ Update Dependencies
- Update dependencies

### 4.2.5

#### 🔥 Code Removal
- Remove ref from typedef as it's included in the React Component interface. #76

### 4.2.4

#### 🐞 Bug Fixes
- Fix typescript definition for event methods.
- Fix a bug where throttled and debounced actions would not take new props.

### 4.2.3

#### 🐞 Bug Fixes
- Fix an issue importing module with typescript. #72

### 4.2.2

#### 🐞 Bug Fixes
- Fix an issue updating state from inside onIdle. #71

### 4.2.1

#### ✨ Enhancements
- Add a typescript definition that will now be maintained along with this library. It expects that you have the react type definitions installed.

#### 📝 Documentation
- Fix a documentation error.

## 4.2.0

#### ⚡️ Features
- Dynamically bind and unbind events.

Events are unbound when:
- `stopOnIdle` is set to `true` and the user goes idle
- `pause()` is called

Events are bound when:
- component is mounted
- `reset()` is called
- `resume()` is called

### 4.1.3

#### 🐞 Bug Fixes
- `stopOnIdle` will now keep `IdleTimer` in idle state until `reset()` is called.

### 4.1.2

#### 🐞 Bug Fixes
- Fix a bug where `stopOnIdle` logic was being applied to active state.

### 4.1.1

#### 🐞 Bug Fixes
- Fix a bug where initial `onIdle` event was not firing when `stopOnIdle` is set

## 4.1.0

#### ⚡️ Features
- Add property `stopOnIdle` defaults to `false`. Setting to `true` will prevent user activity from restarting the `IdleTimer` once it has gone idle.  This useful if you want to do some custom async stuff before the `IdleTimer` gets restarted.  In order to restart the `IdleTimer` call `reset()` on your ref.
- Add event handler `onActive` which enables reporting of all user activity from `IdleTimer`.  The built in `debounce` or `throttle` properties will help increase performance if you are using the `onActive` event. By default `debounce` and `throttle` are off.  Only one can be enabled at a time.
- Add property `debounce` defaults to 0.  Set the `onActive` debounce delay in milliseconds. The `throttle` property cannot be set if this property is set.
- Add property `throttle` defaults to 0.  Set the `onActive` throttle delay in milliseconds.  The `debounce` property cannot be set if this property is set.

### 4.0.9

#### 🐞 Bug Fixes
- Fix a memory leak when IdleTimer is unmounted.

### 4.0.8

#### 🐞 Bug Fixes
- Fix a bug where passive and capture were not being passed to the event listener.

### 4.0.7

#### 🐞 Bug Fixes
- Fix some inconsistencies in the README.

#### 📝 Documentation
- Add default prop values to documentation.

### 4.0.6

#### 🐞 Bug Fixes
- Fix a bug where setting `startOnMount` to `false` starts IdleTimer in the wrong state.

### 4.0.5

#### 🐞 Bug Fixes
- Fix a bug where setting `startOnMount` to `false` starts IdleTimer in the wrong state.

### 4.0.4

#### 🐞 Bug Fixes
- Fix a bug where the module could not be imported.

### 4.0.3

#### 📝 Documentation
- Minor documentation updates.

#### 💚 CI
- Continuous integration bugfixes.

### 4.0.2

#### 📝 Documentation
- Minor documentation updates

#### 💚 CI
- Continuous integration bugfixes

### 4.0.1

#### 📝 Documentation
- Minor documentation updates

#### 💚 CI
- Continuous integration bugfixes

## 4.0.0

Version 4.0 contains a rewrite of the build system and a refactor of the source 
code for IdleTimer. After accepting many pull requests, the projects code style 
was destroyed, so some forced styling was added and PRs that don't respect this 
style will not be accepted. Contribution guide now on the README.  

#### 🔥 Code Removal
- The property `startOnLoad` has been renamed to `startOnMount` to make more sense in a react context.
- The property `activeAction` has been renamed to `onActive`.
- The property `idleAction` has been renamed to `onIdle`.

#### ✨ Enhancements
- Add [passive](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener) property.  Defaults to `true`, bind events with passive mode enabled.
- Add [capture](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener) property.  Defaults to `true`, bind events with capture mode enabled.
- Pass event through to `onActive` callback functions.

#### 🐞 Bug Fixes
- Fixed installation bug on windows machines. This was due to the use of environment variables in the build scripts. The new build system does not rely on environment variables defined at the cli level

## 3.0.0

Dropped support for date formatting in version 3. IdleTimer returns raw 
date objects and you can use which ever library you like to format it. If you 
would like to continue using the built in formatter, stick with version 2.

#### 🔥 Breaking Changes
- Removed built in date formatter.

## 2.0.0

#### ⚡️ Features
- Add support for server side rendering.

## 1.0.0

#### 🚀 Genesis

Initial release.
