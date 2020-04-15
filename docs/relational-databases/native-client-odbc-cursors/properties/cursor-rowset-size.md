---
title: Размер Cursor Rowset (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7f799722bfae35a714e740691e2cdc53e3155063
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302891"
---
# <a name="cursor-rowset-size"></a>Размер набора строк курсора
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Возможности курсоров ODBC не ограничены выбором только одной строки за один раз. Они могут получить несколько строк в каждом вызове на **S'LFetch** или [S'LFetchScroll.](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) При работе с базой данных Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в режиме клиент-сервер значительно эффективнее извлекать несколько строк за один раз. Количество строк, возвращенных на получение, называется размером рядового и указывается с помощью SQL_ATTR_ROW_ARRAY_SIZE [S'LSetStmtAttr.](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 Курсоры, имеющие размер набора строк более 1, называются блочными курсорами.  
  
 Есть два параметра привязки результирующего набора строк для блочных курсоров.  
  
-   Привязка на уровне столбца  
  
     Каждый столбец привязывается к массиву переменных. Число элементов в каждом массиве равно размеру набора строк.  
  
-   Привязка на уровне строки  
  
     Массив создается с использованием структур, которые содержат данные и индикаторы для всех столбцов в строке. Число структур в массиве равно размеру набора строк.  
  
 При использовании прививке столбцов или строки используется привязка к столбцовой или строке, каждый вызов в **S'LFetch** или **S'LFetchScroll** заполняет связанные массивы с данными из извлеченного набора строк.  
  
 [Кроме](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) того, для извлечения данных столбцов из курсора блоков можно также использовать данные столбцов. Так как **S'LGetData** работает по одной строке за раз, **sLSetPos** должны быть вызваны, чтобы установить определенную строку в строке, как текущий ряд, прежде чем вызывать **S'LGetData**.  
  
 Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC предлагает оптимизацию с помощью рядов для быстрого получения набора результатов. Чтобы использовать эту оптимизацию, установите атрибуты курсора на их значения по умолчанию (только вперед, только для чтения, размер строки No 1) в момент вызова **S'LExecDirect** или **S'LExecute.** Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC настраивает набор результатов по умолчанию. Это более эффективно, чем использование серверных курсоров при передаче результатов клиенту без прокрутки. После выполнения инструкции увеличьте размер набора строк и примените привязку на уровне столбца или строки. Это [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] позволяет использовать набор результатов по умолчанию для эффективной [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отправки строк результата клиенту, в то время как драйвер Native Client ODBC непрерывно вытягивает строки из сетевых буферов на клиенте.  
  
## <a name="see-also"></a>См. также:  
 [Свойства курсора](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
