---
title: OCR | Microsoft Docs
description: OCR Actions Reference
author: mariosleon
ms.service: power-automate
ms.subservice: desktop-flow
ms.topic: article
ms.date: 12/02/2020
ms.author: marleon
ms.reviewer:
search.app: 
  - Flow
search.audienceType: 
  - flowmaker
  - enduser
---

# OCR

Initiate OCR engines to perform OCR related activities

|<!-- --> |
|-----|
|[If text on screen (OCR)](#iftextonscreenaction)|
|[Wait for text on screen (OCR)](#waittextonscreenaction)|
|[Create Tesseract OCR engine](#createtesseractocrenginebase)|
|[Create MODI OCR engine](#createmodiengine)|
|[Extract text with OCR](#extracttextwithocr)|

## Getting started with OCR actions

Power Automate enables users to read, extract, and manage data within an assortment of files through optical character recognition (OCR).

To create an OCR engine and extract text from images and documents with OCR, use the **Extract text with OCR** action. In the figure below, the engine is created for the purpose of this action alone, and the OCR source is a locally stored image. The action is set to extract text from the entire image. 

![extract text with ocr action properties screenshot.](\media\ocr\extract-text-ocr-example.png)

The action wherein the OCR engine is created contains the engine settings. These include the language and the image width and height multipliers. The OCR engine variable can be used in any action containing OCR capabilities.

> [!WARNING]
> Image multipliers increase the size of the image to make searching and text extraction more effective. Please note that setting values greater than 3 may lead to erroneous results.


## OCR actions

### <a name="iftextonscreenaction"></a> If text on screen (OCR)
Marks the beginning of a conditional block of actions depending on whether a given text appears on the screen or not, using OCR

##### Input Parameters
|Argument|Optional|Accepts|Default Value|Description|
|-----|-----|-----|-----|-----|
|If text|N/A|Exists, Doesn't exist|Exists|Specifies whether to check if the text exists or not on the given source to analyze|
|OCR engine type|No|OCR engine variable, Tesseract engine|OCR engine variable|The OCR engine type to use. Select a peconfigured OCR engine or set up a new one.|
|OCR engine variable|No|OCREngineObject||The engine to use for the OCR operation|
|Text to find|No|Text value||The text to search for in the specified source|
|Is regular expression|N/A|Boolean value|False|Specifies whether to use a regular expression to find the specified text|
|Search for text on|N/A|Entire screen, Foreground window|Entire screen|Specifies whether to search for the specified text on the entine visible screen or just the foreground window|
|Search mode|N/A|Whole of specified source, Specific subregion only, Subregion relative to image|Whole of specified source|Specifies whether to scan the entire screen (or window) or a narrowed down subregion of it|
|Image(s)|No|List of Image||The image(s) specifying the subregion (relative to the top left corner of the image) to scan for the supplied text|
|X1|Yes|Numeric value||The start X coordinate of the subregion to scan for the supplied text|
|Tolerance|Yes|Numeric value|10|Specifies how much the image(s) searched for can differ from the originally chosen image|
|Y1|Yes|Numeric value||The start Y coordinate of the subregion to scan for the supplied text|
|X1|Yes|Numeric value||The start X coordinate of the subregion relative to the specified image to scan for the supplied text|
|X2|Yes|Numeric value||The end X coordinate of the subregion to scan for the supplied text|
|Y1|Yes|Numeric value||The start Y coordinate of the subregion relative to the specified image to scan for the supplied text|
|Y2|Yes|Numeric value||The end Y coordinate of the subregion to scan for the supplied text|
|X2|Yes|Numeric value||The end X coordinate of the subregion relative to the specified image to scan for the supplied text|
|Y2|Yes|Numeric value||The end Y coordinate of the subregion relative to the specified image to scan for the supplied text|

> [!NOTE]
> Power Automate's regular expression engine is .NET. You can find more information in [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).


##### Variables Produced
|Argument|Type|Description|
|-----|-----|-----|
|LocationOfTextFoundX|Numeric value|The X coordinate of the point where the text appears on the screen. If the search is performed in the foreground window, the coordinate returned is relative to the top left corner of the window|
|LocationOfTextFoundY|Numeric value|The X coordinate of the point where the text appears on the screen. If the search is performed in the foreground window, the coordinate returned is relative to the top left corner of the window|


##### <a name="iftextonscreenaction_onerror"></a> Exceptions
|Exception|Description|
|-----|-----|
|Can't check if text exists in non interactive mode|Indicates that it isn't possible to check for the text on the screen when in non-interactive mode|
|Invalid subregion coordinates|Indicates that the specified subregion coordinates are invalid|
|Failed to analyze text with OCR|Indicates an error occured while trying to analyze the text using OCR|
|OCR engine not alive|Indicates that the OCR engine isn't alive|


### <a name="waittextonscreenaction"></a> Wait for text on screen (OCR)
Wait until a specific text appears/disappears on the screen, on the foreground window, or relative to an image on the screen or foreground window using OCR

##### Input Parameters
|Argument|Optional|Accepts|Default Value|Description|
|-----|-----|-----|-----|-----|
|Wait for text to|N/A|Appear, Disappear|Appear|Specifies whether to wait for the text to appear or disappear|
|OCR engine type|No|OCR engine variable, Tesseract engine|OCR engine variable|The OCR engine type to use. Select a peconfigured OCR engine or set up a new one.|
|OCR engine variable|No|OCREngineObject||The engine to use for the OCR operation|
|Text to find|No|Text value||The text to search for in the specified source|
|Is regular expression|N/A|Boolean value|False|Specifies whether to use a regular expression to find the specified text|
|Search for text on|N/A|Entire screen, Foreground window|Entire screen|Specifies whether to search for the specified text on the entine visible screen or just the foreground window|
|Search mode|N/A|Whole of specified source, Specific subregion only, Subregion relative to image|Whole of specified source|Specifies whether to scan the entire screen (or window) or a narrowed down subregion of it|
|Image(s)|No|List of Image||The image(s) specifying the subregion (relative to the top left corner of the image) to scan for the supplied text|
|X1|Yes|Numeric value||The start X coordinate of the subregion to scan for the supplied text|
|Tolerance|Yes|Numeric value|10|Specifies how much the image(s) searched for can differ from the originally chosen image|
|Y1|Yes|Numeric value||The start Y coordinate of the subregion to scan for the supplied text|
|X1|Yes|Numeric value||The start X coordinate of the subregion relative to the specified image to scan for the supplied text|
|X2|Yes|Numeric value||The end X coordinate of the subregion to scan for the supplied text|
|Y1|Yes|Numeric value||The start Y coordinate of the subregion relative to the specified image to scan for the supplied text|
|Y2|Yes|Numeric value||The end Y coordinate of the subregion to scan for the supplied text|
|X2|Yes|Numeric value||The end X coordinate of the subregion relative to the specified image to scan for the supplied text|
|Y2|Yes|Numeric value||The end Y coordinate of the subregion relative to the specified image to scan for the supplied text|

> [!NOTE]
> Power Automate's regular expression engine is .NET. You can find more information in [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).


##### Variables Produced
|Argument|Type|Description|
|-----|-----|-----|
|LocationOfTextFoundX|Numeric value|The X coordinate of the point where the text appears on the screen. If the search is performed in the foreground window, the coordinate returned is relative to the top left corner of the window|
|LocationOfTextFoundY|Numeric value|The X coordinate of the point where the text appears on the screen. If the search is performed in the foreground window, the coordinate returned is relative to the top left corner of the window|


##### <a name="waittextonscreenaction_onerror"></a> Exceptions
|Exception|Description|
|-----|-----|
|Can't check if text exists in non interactive mode|Indicates that it isn't possible to check for the text on the screen when in non-interactive mode|
|Invalid subregion coordinates|Indicates that the specified subregion coordinates are invalid|
|Failed to analyze text with OCR|Indicates an error occured while trying to analyze the text using OCR|
|OCR engine not alive|Indicates that the OCR engine isn't alive|


### <a name="createtesseractocrenginebase"></a> Create Tesseract OCR engine
Create a Tesseract OCR engine

> [!NOTE]
> The **MODI OCR engine** and the **Create Tesseract OCR engine** action are planned for deprecation. You can find more information about the deprecation in the [respective blog post](https://powerusers.microsoft.com/t5/Power-Automate-Community-Blog/Announcing-deprecation-of-MODI-OCR-engine-and-Create-Tesseract/ba-p/941316#M1186).

##### Input Parameters
|Argument|Optional|Accepts|Default Value|Description|
|-----|-----|-----|-----|-----|
|Use other language|N/A|Boolean value|False|Specifies whether to use a language not given in the choices|
|Tesseract language|N/A|English, German, Spanish, French, Italian|English|The language of the image's text that the Tesseract engine detects|
|Language abbreviation|No|Text value||The Tesseract abbreviation of the language to use. For example, if the data is 'eng.traineddata', enter 'eng' in the field|
|Language data path: |No|Folder||The path of the folder that holds the specified language Tesseract's data|
|Image width multiplier|Yes|Numeric value|1|The image's width multiplier|
|Image height multiplier|Yes|Numeric value|1|The image's height multiplier|


##### Variables Produced
|Argument|Type|Description|
|-----|-----|-----|
|OCREngine|OCREngineObject|The OCR engine for use with later OCR actions|


##### <a name="createtesseractocrenginebase_onerror"></a> Exceptions
|Exception|Description|
|-----|-----|
|Failed to create the OCR engine|Indicates an error occurred while trying to create the OCR engine|
|Data path folder doesn't exist|Indicates that the folder specified for the language data doesn't exist|

##### <a name="createtesseractocrenginebase_DeprecationInfo"></a> Prepare flows for upcoming deprecation

The **Create Tesseract OCR engine** action is planned for deprecation. To prevent flows from failing after the depreciation, initialize the required Tesseract OCR engines directly through the actions that use them.

This OCR engine initialization method provides the same configuration options as before and eliminates the need for a produced **OCREngine** variable.

![The Tesseract OCR engine options in the Extract text with OCR action.](media/ocr/initialize-tesseract-ocr-engine.png)

### <a name="createmodiengine"></a> Create MODI OCR engine
Create a MODI OCR engine

> [!NOTE]
> The **MODI OCR engine** and the **Create Tesseract OCR engine** action are planned for deprecation. You can find more information about the deprecation in the [respective blog post](https://powerusers.microsoft.com/t5/Power-Automate-Community-Blog/Announcing-deprecation-of-MODI-OCR-engine-and-Create-Tesseract/ba-p/941316#M1186).

##### Input Parameters
|Argument|Optional|Accepts|Default Value|Description|
|-----|-----|-----|-----|-----|
|MODI language|N/A|Chinese simplified, Chinese traditional, Czech, Danish, Dutch, English, Finnish, French, German, Greek, Hungarian, Italian, Japanese, Korean, Norwegian, Polish, Portuguese, Russian, Spanish, Swedish, Turkish|English|The language of the image's text that the MODI engine detects|
|Image width multiplier|Yes|Numeric value|1|The image's width multiplier|
|Image height multiplier|Yes|Numeric value|1|The image's height multiplier|


##### Variables Produced
|Argument|Type|Description|
|-----|-----|-----|
|OCREngine|OCREngineObject|The OCR engine to use with later OCR actions|


##### <a name="createmodiengine_onerror"></a> Exceptions
|Exception|Description|
|-----|-----|
|Failed to create the OCR engine|Indicates an error occurred while trying to create the OCR engine|

##### <a name="createmodiengine_DeprecationInfo"></a> Prepare flows for upcoming deprecation

The MODI OCR engine is planned for deprecation. To prevent flows from failing after the depreciation, replace the initialized MODI engines with Tesseract engines.

You can perform the initialization directly through the actions that require the engines without using the **Create Tesseract OCR engine** action.

![The Tesseract OCR engine options in the Extract text with OCR action.](media/ocr/initialize-tesseract-ocr-engine.png)

### <a name="extracttextwithocr"></a> Extract text with OCR
Extract text from a given source using the given OCR engine

##### Input Parameters
|Argument|Optional|Accepts|Default Value|Description|
|-----|-----|-----|-----|-----|
|OCR engine|No|OCR engine variable, Tesseract engine|OCR engine variable|The OCR engine type to use. Select a preconfigured OCR engine or set up a new one.|
|OCR engine variable|No|OCREngineObject||The engine to use for the OCR operation|
|OCR source|N/A|Screen, Foreground window, Image on disk|Screen|The source of the image to perform the OCR operation on|
|Image file path|No|File||The path of the image to perform the OCR operation on|
|Search mode|N/A|Whole of specified source, Specific subregion only, Subregion relative to image|Whole of specified source|The selected mode for the OCR operation|
|Image|No|List of Image||The image to use for narrowing down the scan to a subregion that is relative to the specified image|
|Tolerance|Yes|Numeric value|10|Specifies how much the image can differ from the originally chosen image|
|X1|Yes|Numeric value||The start X coordinate of the subregion to narrow down the scan|
|X2|Yes|Numeric value||The end X coordinate of the subregion to narrow down the scan|
|Y1|Yes|Numeric value||The start Y coordinate of the subregion to narrow down the scan|
|Y2|Yes|Numeric value||The end Y coordinate of the subregion to narrow down the scan|
|Wait for image to appear|N/A|Boolean value|False|Whether to wait for the image to appear on the screen or foreground window|
|Timeout|Yes|Numeric value|0|Specifies the time to wait for the operation to complete before the action fails|


##### Variables Produced
|Argument|Type|Description|
|-----|-----|-----|
|OcrText|Text value|The result after the text extraction|


##### <a name="extracttextwithocr_onerror"></a> Exceptions
|Exception|Description|
|-----|-----|
|Failed to extract text with OCR|Indicates an error occurred while trying to extract text with OCR from the given source|
|Image file not found|Indicates that the file doesn't exist on the given path|
|Landmark image not found |Indicates that the landmark image doesn't exist|
|OCR engine not alive|Indicates that the OCR engine isn't alive|
|Can't get text from screen in non-interactive mode|Indicates that it isn't possible to get text from screen when in non-interactive mode|




[!INCLUDE[footer-include](../../includes/footer-banner.md)]