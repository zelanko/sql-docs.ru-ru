---
title: Создание закладок для строк в ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6489fcee1a8faa3f1205c8418e329182c41e376c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705554"
---
# <a name="bookmarking-rows-in-odbc"></a>Создание закладок строк в ODBC
  Закладка представляет собой значение, используемое для идентификации строки данных. Содержание значения закладки понятно только драйверу или источнику данных. Например, оно может быть простым (номером строки) или сложным (адрес на диске). В ODBC приложение запрашивает закладку для конкретной строки, сохраняет ее и передает обратно курсору для возврата к строке.  
  
 При выборке строк с помощью [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)приложение может использовать закладку в качестве основы для выбора начальной строки. Такой способ представляет собой форму абсолютной адресации, поскольку не зависит от текущей позиции курсора. Для прокрутки к строке с закладкой приложение вызывает **SQLFetchScroll** с *фетчориентатион* SQL_FETCH_BOOKMARK. Эта операция использует закладку, на которую указывает атрибут параметра SQL_ATTR_FETCH_BOOKMARK_PTR. Она возвращает набор строк, начинающийся со строки, определяемой закладкой. Приложение может указать смещение для этой операции в аргументе *фетчоффсет* вызова **SQLFetchScroll**. При указании смещения первая строка возвращаемого набора строк определяется сложением числа в аргументе FetchOffset с номером строки, определяемой закладкой. Поставщик OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает только закладки в статических курсорах и курсорах, управляемых набором ключей. Если при включенных закладках запрошен динамический курсор, то вместо него открывается курсор, управляемый набором ключей.  
  
 Закладки также можно использовать с функцией **SQLBulkOperations** для выполнения операций с набором строк, начиная с закладки.  
  
## <a name="see-also"></a>См. также  
 [Прокрутка и выборка строк](../native-client-ole-db-rowsets/fetching-rows.md)  
  
  
