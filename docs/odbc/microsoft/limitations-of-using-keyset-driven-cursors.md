---
title: "Ограничения по использованию управляемые набором ключей курсоры | Документы Microsoft"
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
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 54581e6bf4aceebc50a752ee460458671e8047bd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Ограничения по использованию управляемые набором ключей курсоры
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Необходимо получить один столбец ROWID для опрашиваемой таблицы. Курсор, управляемый набором ключей не может использоваться для соединения, запросы и инструкции, содержащие DISTINCT, GROUP BY, UNION, INTERSECT или минус предложений.  
  
 Кроме того Если приложение использует псевдонимы таблиц, управляемые набором ключей курсоры не будет работать; типы курсора однонаправленные и статические являются обязательными. Использование ключей тип курсора с псевдонимами таблиц вызовет следующую ошибку: «[Microsoft] [драйвер ODBC для Oracle] нельзя использовать курсоры на соединение, с помощью оператора union, intersect или минус, или на доступ только для чтения, результирующий набор.»  
  
> [!NOTE]  
>  Из-за способа, драйвер выполняет инструкцию SQL, который отправляется на сервер Oracle, Oracle внутренним образом возвращает следующее сообщение об ошибке: «ORA-00964: таблицы имя отсутствует в СПИСКЕ.»
