---
title: Пример диагностики драйверов на основе файлов | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 23234a490f664c4be0811152b2b77ae7c0b73761
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069835"
---
# <a name="file-based-driver-diagnostic-example"></a>Пример диагностики драйверов на основе файлов
Файловый драйвер действует как драйвер ODBC, так и как источник данных. Таким образом, он может создавать ошибки и предупреждения как компонент в соединении ODBC и как источник данных. Поскольку это также компонент, который взаимодействует с диспетчером драйверов, он форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например, если драйверу Microsoft® для dBASE не удалось выделить достаточно памяти, он может вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Так как эта ошибка не связана с источником данных, драйвер добавил только префиксы в диагностическое сообщение для поставщика ([Microsoft]) и драйвер ([драйвер ODBC dBASE]).  
  
 Если драйверу не удалось найти файл Employee. dbf, он может вернуть следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Так как эта ошибка связана с источником данных, драйвер добавил в диагностическое сообщение формат файла источника данных ([dBASE]) в качестве префикса. Так как драйвер был также компонентом, который взаимосвязан с источником данных, он добавил префиксы для поставщика ([Microsoft]) и драйвер ([драйвер ODBC dBASE]).
