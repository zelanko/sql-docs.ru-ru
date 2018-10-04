---
title: Ограничения на использование курсоры | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c4910ebd2c6dd988e937f1e9d6a3281bb0e9741
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47668112"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Ограничения на использование курсоров, управляемых ключевым набором
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Необходимо будет извлечь один столбец ROWID для опрашиваемой таблицы. Нельзя использовать курсоры, соединения, запросы и инструкции, содержащие ключевое слово DISTINCT, GROUP BY, UNION, INTERSECT или минус предложения.  
  
 Кроме того Если приложение использует псевдонимы таблиц, управляемые набором ключей курсоры не будет работать; требуются типы последовательного или статических курсоров. С помощью набора ключей тип курсора с псевдонимами таблиц вызовет следующую ошибку: «[Microsoft] [драйвер ODBC для Oracle] нельзя использовать курсоры на соединения, с помощью оператора union, intersect или минус, или на чтение только результирующий набор.»  
  
> [!NOTE]  
>  Из-за того, драйвер выполняет инструкцию SQL, которая отправляется к серверу Oracle, Oracle внутренним образом возвращает следующее сообщение об ошибке: «ORA-00964: таблицы имя не в СПИСКЕ.»
