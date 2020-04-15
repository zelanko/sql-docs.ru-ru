---
title: Подключи к спецификации исходного кода данных Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300344"
---
# <a name="data-source-specification-subkeys"></a>Подразделы спецификации источника данных
Каждый источник данных, перечисленный в подключке ODBC Data Sources, имеет свой собственный подключ. Этот подключ имеет то же название, что и соответствующее значение в подключке ODBC Data Sources. Значения в этом подключке должны уотеивать драйвер DLL и могут уотесы описания источника данных. Если драйвер поддерживает переводчиков, значения могут перечислить имя переводчика по умолчанию, DLL перевода по умолчанию и опцию перевода по умолчанию. Значения могут также перечислять другую информацию, требуемую драйвером для подключения к источнику данных. Например, водителю может потребоваться имя сервера, имя базы данных или имя схемы.  
  
 Форматы значений показаны в следующей таблице. Требуется только значение драйвера.  
  
|Имя|Тип данных|Данные|  
|----------|---------------|----------|  
|Описание|REG_SZ|*Описание*|  
|Драйвер|REG_SZ|*driver-DLL-путь*|  
|TranslationDLL|REG_SZ|*переводчик-DLL-путь*|  
|ПереводНаи|REG_SZ|*переводчик-имя*|  
|ПереводВариант|REG_SZ|*перевод-вариант*|  
|*выбор-значение-имя*|*тип выбора*|*данные о выборе стоимости*|  
  
 Например, предположим, что драйвер сервера S'L Server требует, чтобы имя сервера и флаг для Преобразования OEM для ANSI и определяет значения сервера и OEMTOANSI для них. Предположим также, что источник данных инвентаризации использует microsoft® Code Page Translator для перевода между страницами кода Windows®® Latin 1 (1250) и Multilingual (850). Значения в подключке инвентаризации могут быть следующими:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
