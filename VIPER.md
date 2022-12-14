# Architecture Principles

## View Layer

### Dependencies 
* Could be UIKit or SwiftUI (embeded inside UIController)

### Responsibililies 
* Emit user interaction to Presenter (UI events)
* Display primitive data (String, Int, Or Enum/Struct/Sequence) as received from Presenter

## Presenter

### Dependencies 
* UIBindings (Combine)
* (Business) Entities

### Responsibililies 
* Application Logic - Decide consequence of user action
	* Forwarding user interaction action to business request (to Interactor)
	* Requesting new Navigation Destination (to Router)
	

## Interactor

### Dependencies
* (Business) Entities 

### Responsibililies 
* Hides details of WS Requesting or Storage
* Request raw persistent data (JSON or whatever) reprensented as Value Types only (one request - one Value )
* Construct Entity (Reference or Value types) from retireved raw datas

## Workers 

### Dependencies
* None (Use URLSession Async/Await API)

### Responsibililies 
* Load Raw Data from WebServices or Local Storage
