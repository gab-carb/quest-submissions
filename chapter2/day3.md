Chapter 2 Day 3 - Arrays, Dictionaries, and Optionals


In a script, initialize an array (that has length == 3) of your favourite people, represented as Strings, and log it:
<img width="680" alt="Capture d’écran, le 2022-05-09 à 16 08 46" src="https://user-images.githubusercontent.com/104936636/167495707-f39f4af1-b6c2-4bdc-99ff-6f93721d989f.png">

In a script, initialize a dictionary that maps the Strings Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a UInt64 
that represents the order in which you use them from most to least:
<img width="905" alt="Capture d’écran, le 2022-05-09 à 16 27 03" src="https://user-images.githubusercontent.com/104936636/167495770-b8af240c-9f4f-4a49-8e3c-65d957faf867.png">

Explain what the force unwrap operator ! does, with an example different from the one I showed you:
When accessing a value from a dictionnary, it always give you an optinal, so you need to unwrap it to get the actual type.
<img width="946" alt="Capture d’écran, le 2022-05-09 à 16 35 37" src="https://user-images.githubusercontent.com/104936636/167495978-05a622df-810a-4478-8aff-f2f2094f6190.png">
<img width="676" alt="Capture d’écran, le 2022-05-09 à 16 35 52" src="https://user-images.githubusercontent.com/104936636/167495997-e8deba82-8b7d-4dd4-8eda-5d2d7dbbe193.png">

Using this picture below, explain...

What the error message means:
The return is a String but you are getting an optional string

Why we're getting this error:
You are looking to get the actual type but the dictionnary returns an optional, that can be String or Nil.

How to fix it:
Using the the force unwrap operator ! To get the actual String type.
