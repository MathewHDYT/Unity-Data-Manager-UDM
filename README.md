![Unity Data Manager](https://github.com/MathewHDYT/Unity-Data-Manager-UDM/blob/main/logo.png/)

[![MIT license](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://lbesson.mit-license.org/)
[![Unity](https://img.shields.io/badge/Unity-5.3%2B-green.svg?style=flat-square)](https://docs.unity3d.com/530/)
[![GitHub release](https://img.shields.io/github/release/MathewHDYT/Unity-Data-Manager-UDM/all.svg?style=flat-square)](https://github.com/MathewHDYT/Unity-Data-Manager-UDM/releases/)
[![GitHub downloads](https://img.shields.io/github/downloads/MathewHDYT/Unity-Data-Manager-UDM/all.svg?style=flat-square)](https://github.com/MathewHDYT/Unity-Data-Manager-UDM/releases/)

# Unity Data Manager (UDM)

## Contents
- [Unity Data Manager (UDM)](#unity-data-manager-udm)
  - [Contents](#contents)
  - [Introduction](#introduction)
  - [Installation](#installation)
- [Documentation](#documentation)
  - [Reference to Data Manager Script](#reference-to-data-manager-script)
  - [Public accesible methods](#public-accesible-methods)
  	- [Create New File method](#create-new-file-method)
  	- [Try Read From File method](#try-read-from-file-method)
  	- [Change File Path method](#change-file-path-method)
  	- [Update File Content method](#update-file-content-method)
  	- [Append File Content method](#append-file-content-method)
  	- [Check File Hash method](#check-file-hash-method)
  	- [Delete File method](#delete-file-method)

## Introduction
A lot of games need to save data between multiple game runs, in a small scope this can be done with Unitys [```PlayerPrefs```](https://docs.unity3d.com/2021.2/Documentation/ScriptReference/PlayerPrefs.html) system, if the scope rises tough this small and easily integrated Data Manager can help you create, manage and load data via. files on the system easily and permanently over multiple game sessions.

**Unity Data Manager implements the following methods consisting of a way to:**
- Create and register a new file with the DataManager and the given settings at the given location (see [Create New File method](#create-new-file-method))
- Read the content of a registered file (see [Try Read From File method](#try-read-from-file-method))
- Change the file path of a registered file (see [Change File Path method](#change-file-path-method))
- Change all the content inside of a registered file (see [Update File Content method](#update-file-content-method))
- Append content to a registered file (see [Append File Content method](#append-file-content-method))
- Check the file hash of a registered file (see [Check File Hash method](#check-file-hash-method))
- Delete a registered file and unregister it (see [Delete File method](#delete-file-method))

For each method there is a description on how to call it and how to use it correctly for your game in the given section.

## Installation
**Required Software:**
- [Unity](https://unity3d.com/get-unity/download) Ver. 2020.3.17f1

The Data Manager itself is version independent, as long as the [```JsonUtility```](https://docs.unity3d.com/2021.2/Documentation/ScriptReference/JsonUtility.html) object already exists. Additionally the example project can be opened with Unity itself or the newest release can be downloaded and exectued to test the functionality.

If you prefer the first method, you can simply install the shown Unity version and after installing it you can download the project and open it in Unity (see [Opening a Project in Unity](https://docs.unity3d.com/2021.2/Documentation/Manual/GettingStartedOpeningProjects.html)). Then you can start the game with the play button to test the Data Managers functionality.

To simply use the Data Manager in your own project without downloading the Unity project get the two files in the **Example Project/Assets/Scritps/** called ```DataManager.CS``` and ```FileData.CS``` or alternatively get the file from the newest release (may not include the newest changes) and save them in your own project. Then create a new empty ```gameObject``` and attach the ```DataManager.CS``` script to it.

# Documentation
This documentation strives to explain how to start using the Data Manager in your project and explains how to call and how to use its publicly accesible methods correctly.

## Reference to Data Manager Script
To use the Data Manager to start playing sounds outside of itself you need to reference it. As the Data Manager is a [Singelton](https://stackoverflow.com/questions/2155688/what-is-a-singleton-in-c) this can be done easily when we get the instance and save it as a private variable in the script that uses the Data Manager.

```csharp
private DataManager dm;

private const string saveFile = "save";

private void Start() {
    dm = DataManager.instance;
    // Calling Function in DataManager
    dm.CreateNewFile(saveFile);
}
```

Alternatively you can directly call the methods this is not advised tough, if it is executed multiple times or you're going to need the instance multiple times in the same file.

```csharp
private const string saveFile = "save";

private void Start() {
    // Calling Function in DataManager
    DataManager.CreateNewFile(saveFile);
}
```

## Public accesible methods
This section explains all public accesible methods, especially what they do, how to call them and when using them might be advantageous instead of other methods. We always assume DataManager instance has been already referenced in the script. If you haven't done that already see [Reference to Data Manager Script](#reference-to-data-manager-script).

### Create New File method
**What it does:**
When you want to create and register a new file with the possible options and content you want to write into the file.

**How to call it:**
- ```FileName``` is the name without extension we have given the file we want to register and create
- ```Content``` is the inital data that is saved into the file
- ```DirectoryPath``` is the directory the file should be saved into
- ```FileEnding``` is the extension the file should have
- ```Encryption``` decides wether the given file should be encrypted or not
- ```Hashing``` decides wether the given file should be checked for unexpected changes before using it
- ```Compression``` decides wheter the given file should be compressed or not

```csharp
string fileName = "save";
string content = "";
string directoryPath = Application.persistentData;
string fileEnding = ".txt";
bool encryption = false;
bool hashing = false;
bool compression = false;
dm.CreateNewFile(fileName, content, directoryPath, fileEnding, encryption, hashing, compression);
```

Alternatively you can call the methods with less paramters as some of them have default arguments.

```csharp
string fileName = "save";
dm.CreateNewFile(fileName);
```

**When to use it:**
When you want to register and create a new file with the system so it can be used later.

### Try Read From File method
**What it does:**

**How to call it:**

**When to use it:**

### Change File Path method
**What it does:**

**How to call it:**

**When to use it:**

### Update File Content method
**What it does:**

**How to call it:**

**When to use it:**

### Append File Content method
**What it does:**

**How to call it:**

**When to use it:**

### Check File Hash method
**What it does:**

**How to call it:**

**When to use it:**

### Delete File method
**What it does:**

**How to call it:**

**When to use it:**
