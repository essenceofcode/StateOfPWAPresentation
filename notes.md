XKCD comic while getting ready

Who am I?
	* David Wilson / Full Stack Developer in the Raleigh Area
	* Not an expert in Progressive Web Apps
		* Presenting to learn about them and share knowledge
		* See a lot of advantages and want to implement for my teams applications
	* Please feel free to interrupt

The State of Progressive Web Apps in 2018

	* Background and Overview
		* What are they?
		* Why should we be excited about them?
	* Core Technologies 
		* Service Workers, Manifest, and App Shell Model
	* Vendor Support and New Developments
	* Not a training session 
		* Give enough information to excite / encourage further exploration
		* Hoping to give a in-depth service work presentation later this year
		

Demo - https://app.ft.com - financial times. https://www.trivago.com/code.nasa.gov or twitter?

	* One of the best ways to explain what a PWA is, is just to show some examples.
	* Show service worker registration and manifest in dev tools
	* Compare to https://google.com (offline vs. online)
	* Pin to home and open as an application
	* All of this was possible before - but the cross browser support for W3C standards make it a lot easier and more reliable

What are Progressive Web Apps?

    * Frances Berriman and Alex Russell in 2015
		* Designer and Google Chrome Engineer
	* A core set of technologies for building richer applications using exaperience web technologies.
        * Service workers
        * Application Manifest
        * App Shell Architecture
	* Combines the best of Native and Web Apps
		* Native
			* Rich User Experience 
			* Utilize the native features of the device
		* Web Application
			* Improved delivery mechanism (allows skipping the store)
			* Improved search and discoverability
			* Single development platform
	    * Fulfills initial promise of iPhone
	* Progressive Enhancement
		* Modernizr

Characteristics of a PWA?

	* According to Alex Russel:

		* Responsive: to fit any form factor
		* Connectivity independent: Progressively-enhanced with Service Workers to let them work offline
		* App-like-interactions: Adopt a Shell + Content application model to create appy navigations & interactions
		* Fresh: Transparently always up-to-date thanks to the Service Worker update process
		* Safe: Served via TLS (a Service Worker requirement) to prevent snooping
		* Discoverable: Are identifiable as “applications” thanks to W3C Manifests and Service Worker registration scope allowing search engines to find them
		* Re-engageable: Can access the re-engagement UIs of the OS; e.g. Push Notifications
		* Installable: to the home screen through browser-provided prompts, allowing users to “keep” apps they find most useful without the hassle of an app store
		* Linkable: meaning they’re zero-friction, zero-install, and easy to share. The social power of URLs matters.

To be considered a PWA:
	* Originate from a secure origin. Served over TLS and green padlock displays (no active mixed content).
	* Load while offline (even if only a custom offline page). By implication, this means that progressive web apps require service workers.
	* Reference a web app manifest with at least the four key properties: name, short_name, start_url, and display (with a value of standalone or fullscreen)
	* An icon at least 144×144 large in png format. E.g.: "icons": [ { "src": "/images/icon-144.png", "sizes": "144x144", "type": "image/png" } ]

Why would I want to use them?

	* Better web applications
		* Makes your existing application faster to load and improves user experience
	* Reach a broader audience
		* According to a 2016 comScore report, the average person spends 84% of his time on mobile devices using just the top 5 most popular apps. I’m sorry to say, these are not your apps. On tablets that number is even higher, with 95% of user time spent in the top 5 apps.  The same report also presents figures showing that it is much easier to reach a large audience on a mobile site than in a native app. 
	* Improved delivery - Web vs. Store
		* Store life-cycle - Publishing and Updating
		* Discoverability
		* Always fresh
	* Improved searchability
	* Cross-platform
		* Maintaining multiple versions
		* It's fun to learn new languages and build new apps, but it's not alway good business.

Consider...

	* 65% of users install 0 native apps a month
		* Comscor
	* 84% of users spend time in just 5 apps
	* 95% on tablets!
	* Web sites reach 4.5 times greater
		* There are close to 600 mobile web applications that reach audiences larger than 5 million visitors—nearly 4.5 times greater than the number of native apps with similar audiences. 
		* The top 1,000 mobile web applications have audiences that are almost 3 times the size of the top 1,000, apps and their audiences are growing twice as fast as native app audiences.


Are there any success stories?

	* https://www.pwastats.com/
    * https://pwa.rocks/


Bottom line:
Users are more likely to use your app if:

	* It's easily discoverable
	* Linkable (cross device)
	* It's single click access
	* Load fast
	* Operate off-line

What are the *core* technologies?

	* Service worker
		* Background sync, offline, push notifications, caching
	* Application manifest
	* Push notifications
	* CacheStorage API
		* this is done in the most unopinionated way possible by exposing a number of basic methods, such as the ability to create and open any number of caches, and store, retrieve, or delete responses in them.  
		* By combining service workers with the power of CacheStorage, we can get direct programmatic control over what gets cached, what gets removed from the cache, and which responses are returned from the cache and which are returned from the network.
	* IndexDB
		* transactional
		* object based
		* indexed
		* browser based
		* A general guideline for data storage is that URL addressable resources should be stored with the Cache interface, and other data should be stored with IndexedDB
		* IndexedDB is a NoSQL database. IndexedDB data is stored as key-value pairs in object stores.

Who maintains the standards?

	* World Wide Web Consortium
	* Notification API, Push API, Service Workers, Background Sync, 


This sounds awesome, what's the catch?

	* Still a new technology
		* Gartner's Hype Cycle - https://en.wikipedia.org/wiki/Hype_cycle#/media/File:Hype-Cycle-General.png
	* Changing standards
		* Many of the standards are still in draft and subject to change.
		* The browsers that are currently supporting the standards are in motion.
		* Is Service Worker Ready?  https://jakearchibald.github.io/isserviceworkerready/
	* Functionality still evolving on key platforms.
		* Google has the best support, but Microsoft is embracing PWAs and Apple has even started supporting them.
	* Look and feel
		* Won't look the same as a native application (drop shadows, animation speed, layout, etc)

Why would I build a progressive web app now?

	* Good option for enterprise applications
		* skip the app store
	* Performance, performance, performance - the most important app feature
	* Less expensive to build and deploy
		* Good option for smaller shops
	* Community Momentum / Increasing Support

App Shell

	* Minimum artifacts to load the application
	* Optimize asset loading
	* Determine critical assets  

Service Workers
	* JavaScript Worker
		* It's a JavaScript Worker, so it can't access the DOM directly. Instead, a service worker can communicate with the pages it controls by responding to messages sent via the postMessage interface, and those pages can manipulate the DOM if needed.  Service worker is a programmable network proxy, allowing you to control how network requests from your page are handled.
	* Runs outside the page context
		* It's terminated when not in use, and restarted when it's next needed, so you cannot rely on global state within a service worker's onfetch and onmessage handlers. If there is information that you need to persist and reuse across restarts, service workers do have access to the IndexedDB API.
	* Advanced caching, background sync, and push notifications
		* https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API
		* Background sync is only available in desktop chrome at this time.  It is part of the service worker spec.

Service Workers and Fetch API
	* Diagram and explanation of how service workers provide an event based model for intercepting browser fetch api requests.

Demo: Simple service worker

Advanced Service Worker Topics

	* Versioning 
		* Service worker activation rules and dealing with new state
	* Caching Strategies
		* https://serviceworke.rs/strategy-network-or-cache.html
		* https://developers.google.com/web/tools/workbox/
		* Cache 
		* Cache, falling back to network
		* Network only
		* Cache, then network
	* Background Synchronization
	* Push Notifications
	* Google Workbox  - Workbox is a library that bakes in a set of best practices and removes the boilerplate every developer writes when working with service workers.

Web App Manifest

	* Allows pinning to home screen
	* Simple json file
	* Defines behavior of the application

		* https://developer.mozilla.org/en-US/docs/Web/Manifest
		* https://realfavicongenerator.net/
		* https://www.pwabuilder.com/
		* Generates app manifest and all the icons for different devices / browsers.

Demo: Web App Manifest

Google
	* Industry leading support
		*standards, access to device APIs, and debugging.
	* Less need to publish in the market place
	* Even supports background sync

Microsoft
    * Excellent User Experience
        * Want web apps on windows to be your best experience.
        * Progressive store apps are first class citizens of the MS store - they want your pwa to be your windows store app    
    * Auto discovery or publish to the store
        * PWA Builder - https://www.pwabuilder.com/
	* PWA In-Store Apps are UWP Apps
        * Proliferation of web frameworks and tools makes building UWP apps as a PWA very attractive.	
    * sonarwhal - Scans and tells you how you can make improvements to your site
    PWAs installed on Windows 10 enjoy all the benefits of running as Universal Windows Platform (UWP) apps, including protection through Windows app sandboxing security and full access to Windows Runtime (WinRT) APIs, including those for:
    Controlling device features (such as camera, microphone, GPS)
    Accessing user resources (such as calendar, contacts, documents, music)
    Launching / navigating your app through Cortana voice commands
    Integrating with the Windows OS (through the Windows Action Center, desktop taskbar, and context menus)
    ...and these are only a few of the added possibilities for your PWA on Windows!

    A PWA installed as a Windows 10 app runs independently from the browser, in a standalone (WWAHost.exe process) window.  Has to be installed from the store to become a UWP app and not a web site running in Edge.


Demo - Microsoft Store - MyCARAX
    * Example Windows Store PWA - MyCARFAX
    * mobile.twitter.com - UWP PWA

Apple
	* Basic Support
		* Service worker and app manifest support
		* Improvement since the last presentation but still far behind
	* No prompt to pin
	* Still need some proprietary APIs
	* Bugs
		* https://medium.com/@firt/progressive-web-apps-on-ios-are-here-d00430dee3a7


Determining Capabilities
	* https://whatwebcando.today/
	* https://caniuse.com
	* https://jakearchibald.github.io/isserviceworkerready/


PWA vs SPA
	* Not competing technologies
	* PWA can be used for SPA or Multi-Page Apps
	* Popular Framework Support

Other Supporting Technologies
	* PRPL - Push, Render, Pre-Cache, Lazy-load
	* AMP - Accelerated Mobile Pages
	* HTTP/2 Server Push

Future of the web
	* Accepting Payments with the Payment Request API
	* User Management with the Credential Management API
	* Real-Time Graphics with WebGL
	* Futuristic APIs with Speech Recognition
	* Slick Media Playing UIs
	* Virtual Reality in the Browser with WebVREasy Sharing to and from Your App

Thank you for your time.

* Futher Research 
	* browser storage limits
	* Push notifications
	