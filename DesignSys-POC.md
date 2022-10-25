# POC SwiftUI Design System inside MCHB Legacy App

## Objectives
 * Introduce Design System Approach : Set of UI Component Toolkit, reusable , themable.
 * Stop using old (obsolescent) technologies like Rx (and use SwiftUI instead of UIKit as most as possible)
 
 
 
## Technical constraints  
 * DesignSystem is isolated in its own Swift Module (SPM), dependending only on SwiftUI
 * All asynchronous code should be managed by modern concurency (async-await)
 * DesignSystem component should not make any hypothesis about their view Model. The only hipotheis are the (simple) data that reprensent the  (view) state of the design system component. **ViewModel code should not be part of DesignSystem Component** 


## Architectural constraints

Rem : Apple APIs are not alway very "Clean Arichecture compliants". For ex the property Wrapper @ObservableObject is defined in SwiftUI. So we can't make ViewModel code independandant from UI Framewart as CleanArchi tells us to do. 

Principle that will try to follow : Split the ViewModel in 3 parts 

1. Main ViewModel Code That only rely on Async-Await Code and doesn't do any Rx or Combine

2. An extension that expose (implement) the RX stuff awaited by the Legacy (UIKit) ViewController

3. An(other) extension that expose (implement) the Combine stuff awaited by the modern (DesignSystem/SwiftUI based) View

This way we can structure code strictly 

* Part 1 is always required and is fully UI independant (doesn't import UIKit nor SwiftUI)
* Part 2 & 3 are just "wrappers" to connect to UI. 
* Only one of 2 or 3 is required (dependy of the UIs connected to the ViewModel)


## First Tasks 
 * Define a new Root Tabbar with one tab showing some UIHostingVC and another showing Legacy VC
 * Rewrite one of our Legacy WebService with async-await approach, so that DesignSystem component connect to it (by an intermediate ViewModel)
 * Put some Rx Wraping code around this async-await code, so that legacy ViewModel could use same service.