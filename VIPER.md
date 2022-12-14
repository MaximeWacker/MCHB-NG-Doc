# Architecture Principles

![../Figures/VIPER_Responsibilities_Boundary_details.pdf](./Figures/VIPER_Responsibilities_Boundary_details.pdf)

## View Layer

### Dependencies 
* Could be UIKit or SwiftUI (embeded inside UIController)

### Responsibililies 
* Emit user interaction to Presenter (UI events)
* Update display from ViewState (struc/enum/sequence of primitive data string/Int/Float) as received from Presenter

## Router
### Dependencies 
* Depends on some Injection Factory (Swinject or hand-made Abstract Factory) for the resolving of AbstractTypes -> ConcreteTypes  

### Responsibililies 
* Sets up all the components of the current UseCase (Screen) from Injection Factory
* Handle Navigation Requests (Enums) from current presenter to Instantiate next UseCase Router and give control to it

## Presenter

### Dependencies 
* UIBindings (Combine)
* (Business) Entities

### Responsibililies 
* Application Logic - Decide direct consequences of user actions
	* Forwarding user interaction action to business as request to Interactor
	* Requesting new Navigation Destination to Router
	

## Interactor

### Dependencies
* (Business) Entities 
* Workers

### Responsibililies 
* Hides details of Worker Requesting details (WebServices or Storage
* Request raw persistent data (JSON or whatever) reprensented as Value Types only (one request - one Value )
* Construct Entity (Reference or Value types) from retireved raw datas

## Workers 

### Dependencies
* Associated RawData (Value Types, like result of JSON Decoding)
* None (Use URLSession Async/Await API)

### Responsibililies 
* Load Raw Data from WebServices or Local Storage



