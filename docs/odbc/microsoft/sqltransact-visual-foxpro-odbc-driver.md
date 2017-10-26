---
title: "SQLTransact (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
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
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9b12fa480f4aef8b669bdd57c4322f8d9f736be6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Уровень Core  
  
 Запрашивает операции фиксации или отката для всех активных операций на все дескрипторы инструкций (*hstmt*s), связанных с подключением или для всех подключений, связанных с этим дескриптором среды *henv*. **SQLTransact** работает только для источников данных, которые являются [баз данных](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 В случае фиксации в ручной режим транзакции остается активным; Вы можете выполнить откат транзакции или повторите операцию фиксации. Если операция фиксации не в режиме автоматической транзакции, транзакция откатывается автоматически. транзакция не может быть неактивным.  
  
 Дополнительные сведения см. в разделе [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) в *справочнике программиста ODBC*.

