---
title: "Закрытие курсора | Документы Microsoft"
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
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 05cf8dde95111a9f5b530b37fd9a60356f4b77bf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="closing-the-cursor"></a>Закрытие курсора
После завершения использования курсора приложение вызывает **SQLCloseCursor** для закрытия курсора. Например:  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 До его закрытия курсора, инструкции, на котором открыт курсор не может использоваться для большинства других операций, например для выполнения другой инструкции SQL. Полный список функций, которые могут вызываться, когда курсор открыт см. в разделе [приложение б: ODBC состояния перехода таблицы](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Чтобы закрыть курсор, приложение должно вызывать **SQLCloseCursor**, а не **SQLCancel**.  
  
 Курсоры остаются открытыми, пока они закрыты явным образом, за исключением того, когда транзакция фиксируется или откатывается назад, в этом случае некоторые источники данных закрыть курсор. В частности, достигнут конец результирующего набора, когда **SQLFetch** не вернет значение SQL_NO_DATA, не закрывает курсор. Необходимо явно закрыт даже курсоры в пустых результирующих наборов (результирующих наборов, созданных при инструкция была выполнена успешно, но который вернул ни одной строки).
