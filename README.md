# MCHB 2023 Architectural Evolution
## Goals

### New App architecture for the futur, with main principles :

1.  Respect Clean Architecture SOLID principles :
	1. 	Multiples, well defined layers of responsibilities
	2. 'Micro-feature' oriented : Many small modules (build targets and/or SPMS)
2. Allow mix of Legacy code and New code in same App
	1. Allow to reuse Legacy Code (Rx+UIKit) 'As is'
	2. Allow to develop New Screen with SwiftUI Technology
	3. Allow to develop New Screen with UIKit Technology but with same undernying component as SwiftUI ones, to ease UIKit->SwiftUI latter migration

### Other (side effect) improvements
* Fix Shared & Core Modules sizes, leading to huge build time and Development feedbacks (Previews and unit-tests) 
* Remove strong dependency to RX (on new screens)
* Allow MCHB project to split into MC & HB

## Clean Architecture for iOS : VIPER

![./Figures/VIPER_Responsibilities_Boundary_details.pdf](./Figures/VIPER_Responsibilities_Boundary_details.pdf)

For detailed Presentation See [VIPER Responsibilities Descirption](./VIPER.md)

## Multi Modules implementation

![./Figures/NG_Modules_AccountEx.pdf](./Figures/NG_Modules_AccountEx.pdf)

For detailed Presentation See [Dependency Inversion Guided Modularization (TODO)](./Modularization.md)

## Three types of UseCase implementation
* [Legacy (TODO)](./LeagacyImplementation.md)
* [VIPER UIKit (TODO)](./ViperUIKitImplementtion.md)
* [VIPER SwiftUIb(TODO)](./ViperSwiftUIImplementtion.md)
