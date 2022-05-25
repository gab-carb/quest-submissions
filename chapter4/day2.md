Chapter 4 Day 2 - Capabilities


-What does .link() do?

Lets you expose certain data from your account storage to the public or to a private path.

-In your own words (no code), explain how we can use resource interfaces to only expose certain things to the /public/ path.

By using a resource interface, you can restrict access to the public to anything inside the interface, 
anything else outside of the interface will be avaible to the public.

-Deploy a contract that contains a resource that implements a resource interface. Then, do the following:
<img width="636" alt="Capture d’écran, le 2022-05-25 à 15 46 00" src="https://user-images.githubusercontent.com/104936636/170362900-b3b20b25-1172-49b8-91a7-c003f98fe650.png">


-In a transaction, save the resource to storage and link it to the public with the restrictive interface.
<img width="979" alt="Capture d’écran, le 2022-05-25 à 15 46 36" src="https://user-images.githubusercontent.com/104936636/170362906-d1983e0b-4bbf-4999-a357-a43ce6831503.png">


-Run a script that tries to access a non-exposed field in the resource interface, and see the error pop up.
<img width="1014" alt="Capture d’écran, le 2022-05-25 à 16 20 33" src="https://user-images.githubusercontent.com/104936636/170362933-d9879c5f-d2e6-45be-97b2-69ae29af09eb.png">

<img width="1003" alt="Capture d’écran, le 2022-05-25 à 16 41 02" src="https://user-images.githubusercontent.com/104936636/170363227-544c07ea-2186-4be4-bee7-f9c331c61b77.png">


-Run the script and access something you CAN read from. Return it from the script.
<img width="995" alt="Capture d’écran, le 2022-05-25 à 16 38 04" src="https://user-images.githubusercontent.com/104936636/170362942-9d179dfa-d232-4216-a3fc-3501c5ef0458.png">
