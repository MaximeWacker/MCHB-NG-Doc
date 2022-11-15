# Architecture Principles

## View Layer


### Dependencies 
* Could be UIKit or SwiftUI (embeded inside UIController)

### Responsibililies 
* Emit user interaction to ViewModel (UI events)
* Display primitive data (String, Int, Or Enum/Struct/Sequence)

## ViewModel

### Dependencies 
* UIBindings (Combine)
* (Business) Entities

### Responsibililies 
* Application Logic - Decide consequence of user action
	* Requesting/Formating new data to display (to Repository)
	* Requesting new Navigation Destiation (to Coordinator)
	

## Repository

### Dependencies
* (Business) Entities 

### Responsibililies 
* Hides details of WS Requesting or Storage
* Request raw persistent data (JSON or whatever) reprensented as Value Types only (one request - one Value )
* Construct Entity (Reference or Value types) from retireved raw 

## DataSources 

### Dependencies
* None (Use URLSession Async/Await API)

### Responsibililies 
* Load Raw Data from WebServices or Local Storage