---
title: "Отмена и предоставление прав, при использовании хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b2a34667e08e767a77f31917f5c373b795c7324
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Отзыв и предоставление прав при использовании хранимых процедур
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Драйвер ODBC для Oracle возвращает следующее сообщение об ошибке при предоставляются права пользователя и затем отозван на таблицу, доступ с помощью хранимой процедуры:  
  
 ЗНАЧЕНИЕ SQL_ERROR = 1  
  
 szErrorMsg = «[Microsoft] [драйвер ODBC для Oracle] неверное число параметров»  
  
 szErrorMsg = «[Microsoft] [драйвер ODBC для Oracle] синтаксическая ошибка или нарушение доступа»  
  
 Вызов функции Oracle OCI Odessp() завершается ошибкой в этом сценарии, но необходимо для реализации параметров по умолчанию. После изменения базовой таблицы разрешения хранимая процедура перекомпилируется перед повторным запуском.
