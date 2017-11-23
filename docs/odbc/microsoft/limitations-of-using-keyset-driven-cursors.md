---
title: "Ограничения по использованию управляемые набором ключей курсоры | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 18a0f58ae88da9646ecb98ee899f39fa84f8c0c1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Ограничения по использованию управляемые набором ключей курсоры
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Необходимо получить один столбец ROWID для опрашиваемой таблицы. Курсор, управляемый набором ключей не может использоваться для соединения, запросы и инструкции, содержащие DISTINCT, GROUP BY, UNION, INTERSECT или минус предложений.  
  
 Кроме того Если приложение использует псевдонимы таблиц, управляемые набором ключей курсоры не будет работать; типы курсора однонаправленные и статические являются обязательными. Использование ключей тип курсора с псевдонимами таблиц вызовет следующую ошибку: «[Microsoft] [драйвер ODBC для Oracle] нельзя использовать курсоры на соединение, с помощью оператора union, intersect или минус, или на доступ только для чтения, результирующий набор.»  
  
> [!NOTE]  
>  Из-за способа, драйвер выполняет инструкцию SQL, который отправляется на сервер Oracle, Oracle внутренним образом возвращает следующее сообщение об ошибке: «ORA-00964: таблицы имя отсутствует в СПИСКЕ.»
