---
title: "Подразделы спецификации источника данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61b485f55be504e894754f74c4ab779b9ebbaf5a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="data-source-specification-subkeys"></a>Подразделы спецификации источника данных
Каждый источник данных, перечисленных в подразделе источники данных ODBC имеется подраздел свои собственные. Этот подраздел содержит имя, совпадающее с именем соответствующего значения в подразделе источников данных ODBC. Значения в него необходимо перечислить библиотека DLL драйвера и может содержать описание источника данных. Если драйвер поддерживает трансляторы, значения может содержать имя преобразователь по умолчанию, перевод DLL по умолчанию и параметр преобразования по умолчанию. Значения могут содержаться и другие сведения, необходимые драйверу для подключения к источнику данных. Например драйвер может потребоваться имя сервера, имя базы данных или имя схемы.  
  
 Форматы значений, как показано в следующей таблице. Только драйвер значение является обязательным.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|Description|REG_SZ|*Описание*|  
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

