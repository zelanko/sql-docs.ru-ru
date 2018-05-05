---
title: Подразделы спецификации источника данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a25c749996f6d57257f532460396384f3dab28ca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="data-source-specification-subkeys"></a>Подразделы спецификации источника данных
Каждый источник данных, перечисленных в подразделе источники данных ODBC имеется подраздел свои собственные. Этот подраздел содержит имя, совпадающее с именем соответствующего значения в подразделе источников данных ODBC. Значения в него необходимо перечислить библиотека DLL драйвера и может содержать описание источника данных. Если драйвер поддерживает трансляторы, значения может содержать имя преобразователь по умолчанию, перевод DLL по умолчанию и параметр преобразования по умолчанию. Значения могут содержаться и другие сведения, необходимые драйверу для подключения к источнику данных. Например драйвер может потребоваться имя сервера, имя базы данных или имя схемы.  
  
 Форматы значений, как показано в следующей таблице. Только драйвер значение является обязательным.  
  
|Название|Тип данных|Данные |  
|----------|---------------|----------|  
|Описание|REG_SZ|*Описание*|  
|Драйвер|REG_SZ|*путь к библиотеке DLL драйвера*|  
|TranslationDLL|REG_SZ|*путь к библиотеке DLL переводчик*|  
|TranslationName|REG_SZ|*Имя преобразователя*|  
|TranslationOption|REG_SZ|*параметр миграции*|  
|*OPT значение name*|*OPT типа значения*|*OPT значение данных*|  
  
 Предположим, например, драйвер SQL Server требуется имя сервера и флаг для OEM в ANSI, преобразование и определяет сервер и OEMTOANSI значения для этих. Также предположим, что источник данных инвентаризации использует преобразователь кодовых страниц Microsoft® для преобразования между Windows® латиница 1 (1250) и многоязыкового (850) кодовые страницы. Значения в подразделе запасов может выглядеть следующим образом:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
