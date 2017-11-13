---
title: "Закладка типы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a4ab42d7a8b18ebb2b37c871f46981c69c84b908
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="bookmark-types"></a>Типы закладки
Все закладки в ODBC 3*.x* закладок переменной длины. Это позволяет первичный ключ или уникальный индекс, связанный с таблицей, чтобы использоваться в качестве закладки. Закладки также можно 32-разрядное значение, которое использовалось в ODBC 2. *x*. Чтобы использовать закладку с курсором, а ODBC 3*.x* приложение устанавливает атрибут инструкции SQL_ATTR_USE_BOOKMARK SQL_UB_VARIABLE. Автоматически используется закладки переменной длины.  
  
 Приложение может вызвать **SQLColAttribute** с *FieldIdentifier* аргументу присвоено SQL_DESC_OCTET_LENGTH для получения длины закладки. Поскольку закладки переменной длины может быть значение типа long, приложению не следует подключить столбец 0, если только он будет использовать закладку для многих строк в наборе строк.  
  
 Закладки фиксированной длины, поддерживаются только для обратной совместимости. Если ODBC 2. *x* приложения, работа с ODBC 3*.x* драйвер вызывает **SQLSetStmtOption** присваивается SQL_USE_BOOKMARKS SQL_UB_ON, он сопоставлен диспетчера драйверов для SQL_UB_VARIABLE . Используется закладки переменной длины, даже если заполняются только 32 бита его. Если драйвер поддерживает закладки фиксированной длины, он будет поддерживать закладки переменной длины. Если ODBC 3*.x* приложения, работа с ODBC 2. *x* драйвер вызывает **SQLSetStmtAttr** присваивается SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, он сопоставлен диспетчера драйверов для SQL_UB_ON и используется 32-разрядных закладки фиксированной длины. Атрибут инструкции SQL_ATTR_FETCH_BOOKMARK_PTR затем должен указывать на 32-разрядных закладки. Если используется закладки длиннее 32 бита, например, если первичные ключи используются в качестве закладок, курсор необходимо сопоставить фактические значения 32-разрядных значений. Например, то построение хэш-таблицы из них. Когда ODBC 3*.x* приложения, работа с ODBC 2. *x* драйвер привязывает закладки, длина буфера должна быть 4.

