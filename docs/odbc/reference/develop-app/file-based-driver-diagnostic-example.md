---
title: Файл-на основе драйвера Диагностический пример (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f09e4f4758b6276836b08f02b24fb31dd1fadc7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305642"
---
# <a name="file-based-driver-diagnostic-example"></a>Пример диагностики драйверов на основе файлов
Драйвер на основе файлов выполняет как драйвер ODBC, так и источник данных. Таким образом, он может генерировать ошибки и предупреждения как в качестве компонента в подключении ODBC, так и в качестве источника данных. Поскольку он также является компонентом, который взаимодействует с менеджером драйвера, он форматирует и возвращает аргументы для **S'LGetDiagRec.**  
  
 Например, если драйвер Microsoft® для dBASE не может выделить достаточную память, он может вернуть следующие значения из **S'LGetDiagRec:**  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Поскольку эта ошибка не была связана с источником данных, драйвер добавил только префиксы в диагностическое сообщение для поставщика («Microsoft») и драйвера («ODBC dBASE Driver»).  
  
 Если водитель не смог найти файл Employee.dbf, он может вернуть следующие значения из **S'LGetDiagRec:**  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Поскольку эта ошибка была связана с источником данных, драйвер добавил формат файла источника данных (dBASE) в качестве приставки к диагностическому сообщению. Поскольку драйвер также был компонентом, который взаимодействовал с источником данных, он добавил префиксы для поставщика («Microsoft») и драйвера («ODBC dBASE Driver»).
