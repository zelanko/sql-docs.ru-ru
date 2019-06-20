---
title: Выбор и обновление наборов строк (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [ODBC]
ms.assetid: cf0eb3b4-8b72-49fc-a845-95edc360cf93
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f04184e968b60a58c4adfa067d516b58b0a43292
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200450"
---
# <a name="fetch-and-update-rowsets-odbc"></a>Выбор и обновление наборов строк (ODBC)
    
### <a name="to-fetch-and-update-rowsets"></a>Получение и обновление наборов строк  
  
1.  Можно также вызвать [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) с SQL_ROW_ARRAY_SIZE, чтобы изменить число строк (R) в наборе строк.  
  
2.  Вызовите [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) или [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) , чтобы получить набор строк.  
  
3.  Если используются связанные столбцы, используйте для набора строк значения данных и длины данных, доступные теперь в буферах связанных столбцов.  
  
     Если используются несвязанные столбцы, вызовите для каждой строки [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) с параметром SQL_POSITION, чтобы установить позицию курсора, а затем выполните следующие действия для каждого несвязанного столбца.  
  
    -   Вызовите [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) один или более раз, чтобы получить данные для несвязанных столбцов после последнего связанного столбца в наборе строк. Вызовы [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) должны происходить в порядке возрастания номеров столбцов.  
  
    -   Получение данных из столбца типа text или image производится многократным вызовом функции [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) .  
  
4.  Настройте текстовые столбцы или столбцы изображений, получающие данные во время выполнения.  
  
5.  Используйте вызовы [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) или [SQLBulkOperations](https://go.microsoft.com/fwlink/?LinkId=58398) для установки положения курсора, обновления, удаления или добавления строк в наборе строк.  
  
     Если для операций обновления и удаления используются текстовые столбцы или столбцы изображений, получающие данные во время выполнения, обработайте их.  
  
6.  Выполните инструкцию позиционирования UPDATE или DELETE, задав имя курсора (его можно получить с помощью [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md)) и используя дескриптор другой инструкции в том же соединении (необязательно).  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций по курсорам &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)  
  
  
