---
title: Закрытие курсора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 632a922abb544a379892dfa168f55efd605304c8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63125440"
---
# <a name="closing-the-cursor"></a>Закрытие курсора
Когда приложение завершило использование курсора, он вызывает **SQLCloseCursor** для закрытия курсора. Пример:  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 До его закрытия курсора, инструкции, на котором курсор открыт, не может использоваться для большинства других операций, такие как выполнение другой инструкции SQL. Полный список функций, которые могут вызываться, когда курсор открыт, см. в разделе [приложении б: Таблицы перехода состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Чтобы закрыть курсор, приложение должно вызывать **SQLCloseCursor**, а не **SQLCancel**.  
  
 Курсоры остаются открытыми, пока они закрыты явным образом, за исключением того, когда транзакция фиксируется или откатывается назад, в этом случае некоторые источники данных закрыть курсор. В частности, достигнут конец результирующего набора, когда **SQLFetch** не вернет значение SQL_NO_DATA, не закрывает курсор. Даже курсоры в пустых результирующих наборов (результирующих наборов, созданных при инструкция выполнена успешно, но который вернул ни одной строки) должны быть закрыты явным образом.
