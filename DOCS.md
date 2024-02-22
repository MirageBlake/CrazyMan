# _**Mirage Engine Python 2024**_ (V1) - Documentation
##### _**Also known as the engine that runs CrazyMan 0.0.1**_

## Introduction
_Mirage Engine Python 2024_ (V1), or what we will proceed to call _MEP1_ throughout the documentation, is coded strictly in Python using preinstalled libraries. This engine was created to help ease the creation of Text-Based video games in Python's native console. Its most notable use is in the game _CrazyMan_, the game the engine was originally programmed for. _**Note that it's not only meant for CrazyMan; you can create other games using it.**_

## Core Concepts
_MEP1_ has 5 core features to ease the development of text-based games in Python:

* __Save__
* __Load__
* __Console Colors/Effects__
* __Cleanse__
* __ChoiceList__
* __Save__

## Save

_MEP1_ uses Python dictionaries for saving user data while the game is active. When the game isn't active, these dictionaries can be saved through the save function.

```python
# In a manner like this
csave('czms', save)
```

Let's break that down. The save function is named `csave` because of already existing function names; the "c" stands for Crazy. The save function's first parameter is the file that the dictionary will be saved to. It will default to "czms" if nothing is entered. "czms" stands for CrazyManSave; due to the nature of the engine, we thought it appropriate to name the files by default after CrazyMan. The final file will look something like this: `czms.json`. This file will be created by default thanks to Python; no need to worry about that. The second parameter, in this case, `save`, is the Python dictionary. You can name the dictionary whatever you please. The final file will be a `.json`, like mentioned previously. The reason JSON is used is in case someone rips the code and hosts it online. JSON is way more accessible than Pickle data files, and thanks to Python, writing JSON and reading it is incredibly easy. Plus, it's an added bonus that you can easily modify game saves.

## Load
_MEP1_ uses Python dictionaries for save files like we mentioned in the save section. Now we will go over the way you load the previously saved files.

```python
# You load files with save data like this
save = cload('czms')
```

Let's break that down. The load function is named `cload` because of already existing function names; the "c" stands for Crazy. To properly rewrite the empty dictionary in the game code, we recommend overwriting it with the save data like the example shows. For example, in CrazyMan, loads are executed like this:

```python
global save
save = cload('czms')
```

If you have a lot of global vars, we do not recommend doing this due to Python getting slower with a larger quantity, but CrazyMan has very few, making this the best possible route. The parameter is the name of the JSON file with the dictionary in it, for example: `czms.json`. You do not and should not put `.json` because we are nice. We do support it, but the engine automatically adds `.json` in the load process. It's that simple to load data using _MEP1_.

# Console Colors
_MEP1_ allows coloring of the Python `print` function. It supports 6 colors:

* __Black__
* __Red__
* __Green__
* __Gold__
* __Blue__
* __White__

_MEP1_ has a specific call function for colors to prevent miscalling to allow the code to run even if a color is inputted wrong.

```python
get_color(color_name)
```

Let's break it down. The function has one parameter, that being the color's name in _MEP1_. The color names are as follows:

|*MEP1 Name*|*Actual Color*|
|-------------|:-------------:|
|**black**|*Black*|
|**red**|*Green*|
|**green**|*Gold*|
|**blue**|*Blue*|
|**default**|*Normally White*|

Before we explain the use, what do we mean by *"Normally White"* for default? Well, it depends on the console; most consoles have white text, but it could be different.

```python
print(get_color("red") + "Hello, world!" + get_color("default"))
```

Let's break it down. To use a different color, you put the statement `get_color(color_name)` before the actual message, then add a plus for the message. If you want all of the messages to be that color, ignore `get_color("default")`; this resets the message color back to what it was originally. Otherwise, it will print all future messages as the same color.

## Console Effects
In some cases, like Windows CMD, support text blinking and other effects. _MEP1_ has support for this, but if the OS does not support it, the effect won't show, but you can see the text still just as default text. You can color text while giving it an effect as well. Like colors in _MEP1_, effects are loaded through a function to prevent code failure from misinputted code or non-existent effects.

```python
get_effect(effect_name)
```

Let's break it down. The function has one parameter, `effect_name`. There are 9 supported effects in _MEP1_; here they are with their _MEP1_ names and functions:

|*MEP1 Name*|*Effect Info*|
|-------------|:-------------:|
|**reset**|*Back to normal*|
|**bold**|*Bolds the text*|
|**disable**|*Makes the text look disabled*|
|**underline**|*Underlines the text*|
|**reverse**|*Reverses the text order*|
|**strikethrough**|*Adds a strikethrough to the text*|
|**invisible**|*Hides the text*|
|**blink**|*Causes the text to blink*|
|**default**|*If the effect doesn't exist, sets to reset*|

Here are two uses of the function.

```python
print(get_effect("bold") + get_color("red") + "Hello, world!" + get_color("default") + get_effect("reset"))
print(get_effect("bold") + "Hello, world!" + get_color("default"))
```

Let's break it down. To put an effect, you need to call `get_effect(effect_name)`, then add the message. To end the effect, you need to set the effect to reset like this `get_effect("reset")`. And as you can see, you can add color as well.

## Cleanse

```python
cleanse()
```

The purpose of this function is to clear the entire console. It works on every OS.

## ChoiceList
This is the most well-thought-out function; it allows you to ease the creation of menus like this:

```python
(0). Hello
(1). World
Your Choice:
```

Get ready for an onslaught of explaining.

```python
options = ["option 1", "option 2", "option 3"]
functions = [func1, func2, func3]
choiceList(options, functions)
```

No matter what, the choices will always have the first option as `(0)`. because of the index number of the options; that's how their numbers are assigned. There is no limit on options. You must make an array of options; the function only supports a list. Then you must make another list for what each option does, which would be a function, presumably. If something else works, let us know. Then you add the options list first, then the functions, and it will display like this:

```python
(0). option 1
(1). option 2
(2). option 3
Your Choice:
```

Last Updated: _02/22/24 - Blake Leslie_
