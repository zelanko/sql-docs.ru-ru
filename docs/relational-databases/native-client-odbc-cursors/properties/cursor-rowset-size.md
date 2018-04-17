---
title: Размер набора строк курсора | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8e3f46beeab50b6c98845cbc3a56208c263a8573
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-rowset-size"></a>Размер набора строк курсора
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Возможности курсоров ODBC не ограничены выбором только одной строки за один раз. Они могут извлекать несколько строк в каждом вызове **SQLFetch** или [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). При работе с базой данных Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в режиме клиент-сервер значительно эффективнее извлекать несколько строк за один раз. Число строк, возвращаемых запросом, называется размером набора строк и указывается при помощи параметра SQL_ATTR_ROW_ARRAY_SIZE функции [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
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
  
 При использовании либо на уровне столбца или строки, каждый вызов **SQLFetch** или **SQLFetchScroll** привязанный массив заполняется данными из извлеченного набора строк.  
  
 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) также может использоваться для извлечения данных столбца из блочного курсора. Поскольку **SQLGetData** работает с одной строкой за раз **SQLSetPos** необходимо вызвать, чтобы указывать конкретную строку в наборе строк как текущую строку до вызова метода **SQLGetData**.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента обеспечивает оптимизацию за счет использования наборов строк для извлечения всего результирующего набора быстро. Чтобы использовать эту оптимизацию, установить атрибуты курсоров в значения по умолчанию (однопроходный, только для чтения, размер набора строк = 1) во время **SQLExecDirect** или **SQLExecute** вызывается. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента настраивает результирующий набор по умолчанию. Это более эффективно, чем использование серверных курсоров при передаче результатов клиенту без прокрутки. После выполнения инструкции увеличьте размер набора строк и примените привязку на уровне столбца или строки. Это позволяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использования результирующего набора по умолчанию результирующие строки эффективно отправлять клиенту, пока [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента непрерывно извлекает строки из сетевых буферов на клиенте.  
  
## <a name="see-also"></a>См. также  
 [Свойства курсора](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
