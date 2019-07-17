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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069835"
---
# <a name="file-based-driver-diagnostic-example"></a>Пример диагностики драйверов на основе файлов
Драйверов на основе файла действует как в качестве драйвера ODBC, так и в качестве источника данных. Таким образом создается ошибок и предупреждений, так как компонент в подключение ODBC и в качестве источника данных. Так как это компонент, который взаимодействует с диспетчером драйверов, он форматирует и возвращает аргументы для **SQLGetDiagRec**.  
  
 Например, если драйвер для dBASE Microsoft® не удалось выделить достаточный объем памяти, могут возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Так как эта ошибка не была связана с источником данных, драйвер добавлен только префиксы диагностическое сообщение для поставщика ([Microsoft]) и драйвер ([ODBC драйвер для dBASE]).  
  
 Если драйвер не удалось найти файл Employee.dbf, он может возвращать следующие значения из **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Так как эта ошибка была связана с источником данных, драйвер добавлено формат файла источника данных ([dBASE]) в качестве префикса для диагностическое сообщение. Драйвер также использовался компонент, сопряженный с источником данных, она добавлена префиксы для поставщика ([Microsoft]) и драйвер ([ODBC драйвер для dBASE]).
