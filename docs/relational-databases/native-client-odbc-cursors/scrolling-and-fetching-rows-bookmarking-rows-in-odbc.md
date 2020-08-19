---
description: Прокрутка и выборка строк — создание закладок строк в ODBC
title: Создание закладок для строк в ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e183a969cb6208cebbeef0d5c0fc662f9a93381f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423876"
---
# <a name="scrolling-and-fetching-rows---bookmarking-rows-in-odbc"></a>Прокрутка и выборка строк — создание закладок строк в ODBC
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Закладка представляет собой значение, используемое для идентификации строки данных. Содержание значения закладки понятно только драйверу или источнику данных. Например, оно может быть простым (номером строки) или сложным (адрес на диске). В ODBC приложение запрашивает закладку для конкретной строки, сохраняет ее и передает обратно курсору для возврата к строке.  
  
 При выборке строк с помощью [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)приложение может использовать закладку в качестве основы для выбора начальной строки. Такой способ представляет собой форму абсолютной адресации, поскольку не зависит от текущей позиции курсора. Для прокрутки к строке с закладкой приложение вызывает **SQLFetchScroll** с *фетчориентатион* SQL_FETCH_BOOKMARK. Эта операция использует закладку, на которую указывает атрибут параметра SQL_ATTR_FETCH_BOOKMARK_PTR. Она возвращает набор строк, начинающийся со строки, определяемой закладкой. Приложение может указать смещение для этой операции в аргументе *фетчоффсет* вызова **SQLFetchScroll**. При указании смещения первая строка возвращаемого набора строк определяется сложением числа в аргументе FetchOffset с номером строки, определяемой закладкой. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает только закладки в статических курсорах и курсорах, управляемых набором ключей. Если при включенных закладках запрошен динамический курсор, то вместо него открывается курсор, управляемый набором ключей.  
  
 Закладки также можно использовать с функцией **SQLBulkOperations** для выполнения операций с набором строк, начиная с закладки.  
  
## <a name="see-also"></a>См. также:  
 [Прокрутка и выборка строк](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
  
