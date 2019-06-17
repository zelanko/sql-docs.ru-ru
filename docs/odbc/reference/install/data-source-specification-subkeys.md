---
title: Подразделы спецификации источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad210f91d00f9e692c8ee20fef01a808a01501c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198206"
---
# <a name="data-source-specification-subkeys"></a>Подразделы спецификации источника данных
Каждый источник данных, перечисленных в подразделе источники данных ODBC содержит подраздел свои собственные. Этот подраздел содержит имя, совпадающее с именем соответствующего значения в подразделе источников данных ODBC. Значения в него необходимо перечислить библиотека DLL драйвера и могут быть перечислены описание источника данных. Если драйвер поддерживает преобразователей, значения могут быть перечислены имя преобразователь по умолчанию, по умолчанию преобразование библиотеки DLL и перевод параметр по умолчанию. Значения могут содержаться и другие сведения, необходимые драйверу для подключения к источнику данных. Например драйвер может потребоваться имя сервера, имя базы данных или имя схемы.  
  
 Как показано в следующей таблице, используются форматы значений. Только драйвер значение является обязательным.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|Описание|REG_SZ|*Описание*|  
|Драйвер|REG_SZ|*путь к библиотеке DLL драйвера*|  
|TranslationDLL|REG_SZ|*путь к библиотеке DLL перевода*|  
|TranslationName|REG_SZ|*Имя веб-трансляции*|  
|TranslationOption|REG_SZ|*параметр миграции*|  
|*OPT значение name*|*OPT типа значения*|*OPT значение data*|  
  
 Например предположим, драйвер SQL Server требуется имя сервера и флаг для OEM в ANSI, преобразование и определяет сервер и OEMTOANSI значения для них. Также предположим, что источник данных инвентаризации использует код страницы Microsoft® Translator для преобразования между Windows® латиница 1 (1250) и многоязыкового (850) кодовые страницы. Значения в подразделе запасов может выглядеть следующим образом:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
