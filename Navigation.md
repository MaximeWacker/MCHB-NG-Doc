# Navigation

SwiftUI is a State Driven Declarative API for UI.
The display update is the result app state change. The rules of these changes being expressed as declarative code inside View object.

But this state driven approach also apply for Navigation. In SwiftUI, Navigation is also the result of app change.
Going from screenA to screenB is the result of a app state change that impacts screenA rendering, in such way that it leads to transition to screenB

If we store the availables next (screen) destination in each coordinator (as enum), a DeepLink could then be defined as a sequence of such destination