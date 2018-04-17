---
title: Определение числа затронутых строк | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86408e2c18eb18ef9119d1fa11172e6eb1d674a5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="determining-the-number-of-affected-rows"></a>Определение числа затронутых строк
После приложение обновляет, удаляет или вставляет строки, он может вызвать **SQLRowCount** можно определить затронутые количества строк. **SQLRowCount** возвращает это значение, независимо от наличия строки были обновлены, удалены или вставлены, выполнив **обновление**, **удаление**, или **вставить** инструкции При выполнении позиционированного обновления или удаления инструкции и путем вызова **SQLSetPos**.  
  
 Если выполняется пакет инструкций SQL, количество затронутых строк может быть полный счетчик для всех инструкций в пакете или отдельных счетчиков для каждой инструкции в пакете. Дополнительные сведения см. в разделе [пакеты инструкций SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) и [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Также возвращается число затронутых строк SQL_DIAG_ROW_COUNT диагностические поля в заголовке в области диагностики, связанные с дескриптором инструкции. Тем не менее, данные в этом поле сбрасывается после вызова каждой функции, в том же дескрипторе инструкции, в то время как значение, возвращаемое **SQLRowCount** остается неизменным до вызова **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, или **SQLSetPos**.
