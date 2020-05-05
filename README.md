# AUX Indicators
Current version: 1.0.0  
Last revision: May 5th, 2020 17:08 UTC  
Author: [Paris N. Baltazar Salguero][parisbs]  
Colaborators: Leticia Ramirez Ramirez

## What're AUX Indicators?
Accessibility & Usability Experience Indicators is a tags methodology to make easier the communication between UX and development teams to determine how the features and requirements must be implemented to have a balance between UI experience, functionality with accessibility support and inclusive usability

## How it works?
During the mockups or prototype design the UXs can use this indicators to determine the natural behavior that the feature must have. The indicators contains some main categories to rate this features and notify development team how they must implement the functionality to keep safe accesible behavior. The developers can determine what actions they must take to comply with the accessible behaviors assigned by the UXs calculating with a binary template what's the expected behavior with details for each component or feature

## AUX Indicators tags
### HF
If the component requires an haptic feedback when the user interact with it. Aditionaly you can determine an specific pattern with . (point) and - (dash) symbols where point represents a short feedback (1 second) and dash a long one (3 seconds). Examples:  
HF- determine an haptic feedback with long length, HF.. indicate an haptic pattern of two short consecutive feedbacks.  
*NOTE: HF without points or dashes it's equivalent to an haptic feedback with one short length*

### SF
Indicate that the control will have a sound feedback when the user interact with the component, the sounds must be given by the UX's. Don't use sounds that are more than 3 seconds length or it could affect the experience of some users, this does'nt apply to ambient sounds or musical orchestras for games or to sounds used for alarms, ringtones or similar. Examples:  
SF(https://example.com/send_message_sound.mp3

### T
Determines the duration of any popup message, if you add a P indicates a persistent popup, otherwise use a number in seconds, also you can use S (short), M (medium) or L (long) to determine a default value offered by the platforms like Toast.SHORT_LENGTH, in Android. Examples:  
TP if the popup must be persistent, T5 to show during 5 seconds, TM to use the platform default lengths  
*NOTE: If the popup contains an action button that involves modifying any data that might affect UI flow like "Undo", "Don't remind me again" or "Retry", it should preferably be persistent and have auto focus. This doesn't apply to buttons that represent discard actions for the popup message such as a simple "Ok" or "Accept" button as long as the message doesn't represent an authorization or sign of the user with a legal means, contract or confirmation of changes or transactions*

### AF
If the component requires an auto focus when is showed, only use this in a one component by layout and remenber that a popup it's an individual layout. Useful with forms to enforce the user cursor in a component. Examples:  
In a form with 6 different imputs use AF in the first one, if a popup message is showed when the user press "Next" AF in the popup make the cursor jump to it. If the user have an incorrect input AF jump to the component with problems, if more than one component have problems AF  enforce first one

### SC
Determine a shortcut to active or interact with a component, Use +[shortcut] to indicate the gesture or keystrokes of the shortcut. Examples:  
SC+ALT+K indicate Alt + K key, SC+swipe+up indicates a swipe gesture over the capacitive screen  
*NOTE: the keyboard shortcuts could be supported by smartphones or tablets but depend if the user have this periferics connected or enabled in the device, notify the user for these shortcuts and how to interact with them, also provide a persistant link or button to the user to view the full list of the available shortcuts in the current layout*  
**WARNING: before determine a shortcut please verify if the shortcut don't  make interferences with the most popular assistive softwares like [Freedom Scientific products][freedomscientific], [NVDA software][nvda], Talkback [gestures][tb-gestures] and [keyboard shortcuts][tb-keyboard] for Android or VoiceOver [gestures][vo-gestures] and [keyboard shortcuts][vo-keyboard] for Apple**

### ALT & DC
Use these tags to indicate the alternative text for images or pictures if it's required, also you can indicate if the resource it's only a decorative image. The image description must be the most short and clear possible and only it's required when the image it's the only way to show information or data to the user and if these info are important for the content understanding, otherwise the image can be tagged as decorative. Don't use descriptions without context or non-descriptive texts like "Image with instructions", "Errors list" or "User picture", the first and second should describve the content clearly like "Press next to continue" or "This field only contains numbers between 0 and 9" and the last one it's not necessary so must be declared as decorative. Avoid using expressions like "Image contains", "Image with" or "Image is" for the beginning of descriptions, it doesn't provide valuable information to the user and may affect the flow for some users. Example:  
A logo with DC tag indicates that it's a decorative image, an image with ALT"Image description" determines the alternative text for the resource  
*NOTE: Emogys, stickers or expresive images couldn't consider as decorative because it should provides contextual information for the user and it's recommended to add alternative text and an accessible way to use and insert it for the apps with edit fields with these features*  
**WARNING: all decorative images must be skiped for assistive softwares, specialy for screen readers because their could affect the user experience, please go to the documentation for each platform to determine the way to mark as NOT important for accessibility**

### FI & FG
Determine if the component with childs must allows independent focus for each child or must be consider as one component, useful for mobile layouts where card views can be managed as unique component or not. It's not necessary to tag all the childs, you can use "(FI)" and (/FI)" to determine the begining and the finish of the component and you can nestle other tags inside the component. Example:  
If you have a card view with a character description with the picture, name, kind, and a list of attributes you can put (FI) at the begining of the component and (/FI) at the end to indicate that all the childs must be focusable, and add DC tag to the picture to make it a decorative.  
If you want to make the attributes list focusable as a group you can put (FI) at the begining of the component, (FI) at the end, DC over the picture and (FG) at the begining of the attributes child and (/FG) at the end  
To only mark the name and kind as a sub group, attributes list as another group you must mark the card view as FI because you don't want manage the card view as a unique component so you could have (FI) and (/FI) for card view, DC on picture, (FG) and (/FG) on name and kind, (FG) and (/FG) for attributes list  
*NOTE: it's not recommended to grouping childs with long content like two large texts, it's only recommended for representative lists with short content and only if it's necessary to improve the user experience, for example on a very large lists of numeric values with the format key: value*  
**WARNING: before use these tags please ask to mobile developers for the restrictions to manage these behaviors and how the card views works in specific platforms or languages**

### TAB
Use this tag to change the navigation order of the layout when it's necessary, add a number value begining in one to indicate the correct navigation flow. Example:  
If you layout contains 4 different components but you want to put the 3th before the 2nd you can add TAB1 to the 3th and TAB2 to 2nd, the rest of the flow keeps normaly. Use your keyboard to verify the correct implementation of this feature, almost platforms use the Tab and Shift+Tab keys to navigate between components  
*NOTE: Only recommended when the normal flow can't be equals in visual and assistive software navigation, go to the documentation for most popular softwares to determine if this is necessary or not*  
**WARNING: Some languages and platforms require that the developer determine the tab order for all the components when one use this tag, please go to the platform or language documentation to know the behavior of this feature**

## Accessibility validation tools
You can use these tools to verify the accessibility level of your web or app, fell free to colaborate if you want to add another one

* [Web accessibility checkers and tools recommended by W3C][w3c-web-tools]
* [AccessLint for web projects on GitHub][accesslint]
* [Accessibility on Android by Google][android-accessibility]
* [Blog about how to test accessibility on Android][android-accessibility-testing]
* [Accessibility for developers by Apple][apple-accessibility]
* [Accessibility testing on iOS][ios-accessibility-testing]
* [Blog with mobile accessibility tools][mobile-tools]
* [WCAG 2.1 by W3C][wcag-21]

## How to colaborate?
Create a new pull request with your sugested changes explaining the reasons and your investigation sources to apply new rules, categories or changes

[freedonscientific]: https://www.freedomscientific.com
[nvda]: https://www.nvaccess.org/files/nvda/documentation/userGuide.html
[talkback-gestures]: https://support.google.com/accessibility/android/answer/6151827?hl=en
[talkback-keyboard]: https://support.google.com/accessibility/android/answer/6110948?hl=en
[vo-gestures]: https://www.apple.com/voiceover/info/guide/_1137.html
[vo-keyboard]: https://www.apple.com/voiceover/info/guide/_1131.html
[w3c-web-tools]: https://www.w3.org/WAI/ER/tools/
[accesslint]: https://accesslint.com/
[android-accessibility]: https://developer.android.com/guide/topics/ui/accessibility/testing
[android-accessibility-testing]: https://thoughtbot.com/blog/accessibility-testing-on-android
[apple-accessibility]: https://developer.apple.com/accessibility/
[ios-accessibility-testing]: https://developer.apple.com/library/archive/technotes/TestingAccessibilityOfiOSApps/TestingtheAccessibilityofiOSApps/TestingtheAccessibilityofiOSApps.html
[mobile-tools]: https://www.digitala11y.com/free-mobile-accessibility-testing-tools/
[wcag-21]: https://www.w3.org/TR/WCAG21/

[parisbs]: https://github.com/parisbs
