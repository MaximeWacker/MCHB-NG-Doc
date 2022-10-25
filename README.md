# 2023 MCHB UI & Tech Refactoring



## Current (Legacy) Component
###Shared 
* Additions
	* Constants (Analytics / URls / Tokens / etc)
	* Keys (FeatureFlip / Notif / Service / ... )
	* Lots of Misc Helpers (Logger / Analytics / Scan / Math / ...)
* Components
	* CenteredCollectionViewFlowLayout
* Extensions
	* Misc Helpers as swift Extension ( for Foundation & UIKit objects )

**So *Shared* means 'Constants & Misc Helpers'**
	
#### Dependencies 
* AEP* Adobe Analytics
* RxSwift (very tiny depedency : Need little study for dropping impact)
* RxExt : NOT USED
		
###Core
* Assemblies (Swinject)

	Services and Fetchers Assemblies
	
* Common 

	Various misc def & extension (Session / Account / URL / ...)
	
* Entity

	Structs for JSONs
	
* Service

	All (generated) WS Calls (Rx observable)
	
/!\ What's ExtensionCore (inside Core ?!)
 
**So, *Core* means 'Services & Low Level Business Object** (+ Some various extensions & helpers)
	
#### Dependencies

Hard to drop

* RxSwift : All (generated) Services depend on Rx 
* Swinject / SwinjectAutoregistration : Service Injections
* Flagship (but could/should be isolated)

Dropable

* XMLCoder (to much for the needs ?)
* CryptoSwift (to replace by Apple CryptoKit iOS13+)
* NetFox (to be isolated ?)

Easy to drop

* KeyPathKit : use only once (in BIBank)
* SwiftStomp : use only for WebSocketTelmiBot (obsolete)