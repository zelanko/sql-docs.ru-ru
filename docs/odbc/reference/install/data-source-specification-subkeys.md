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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 281377c307f3f3750e87bf5dc988beb7660067af
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300344"
---
# <a name="data-source-specification-subkeys"></a>Подразделы спецификации источника данных
Каждый источник данных, указанный в подразделе источники данных ODBC, имеет собственный подраздел. Этот подраздел имеет то же имя, что и соответствующее значение в подразделе источники данных ODBC. Значения в этом подразделе должны перечислять библиотеку DLL драйвера и могут выводить описание источника данных. Если драйвер поддерживает переводчики, то значения могут иметь имя транслятора по умолчанию, библиотеку DLL преобразования по умолчанию и параметр преобразования по умолчанию. Значения могут также перечислять другие сведения, необходимые драйверу для подключения к источнику данных. Например, драйверу может потребоваться имя сервера, имя базы данных или имя схемы.  
  
 Форматы значений представлены в следующей таблице. Требуется только значение Driver.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|Описание|REG_SZ|*nописание*|  
|Драйвер|REG_SZ|*Driver-DLL-путь*|  
|транслатиондлл|REG_SZ|*Translator-DLL-путь*|  
|транслатионнаме|REG_SZ|*Имя переводчика*|  
|транслатионоптион|REG_SZ|*Translation-параметр*|  
|*OPT-значение-имя*|*неявное значение-тип*|*неявное значение — данные*|  
  
 Например, предположим, что для драйвера SQL Server требуется имя сервера и флаг для преобразования OEM в ANSI, а также для определения сервера и ОЕМТОАНСИ значений этих параметров. Предположим также, что источник данных инвентаризации использует Транслятор кодовых страниц Microsoft® для преобразования между кодовыми страницами Windows® Latin 1 (1250) и многоязычной (850). Значения в подразделе Inventory могут выглядеть следующим образом:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
