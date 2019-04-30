---
title: Определение количества затронутых строк | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99e3676c3b73b177f5e6fc3acef0d93d55cce898
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63262102"
---
# <a name="determining-the-number-of-affected-rows"></a>Определение числа затрагиваемых строк
После приложение обновляет, удаляет или вставляет строки, оно может вызвать **SQLRowCount** для определения, сколько строк были затронуты. **SQLRowCount** возвращает это значение ли строки были обновлены, удалены или вставлены, выполнив **обновление**, **удалить**, или **вставить** инструкции При выполнении позиционированного обновления или инструкция delete или путем вызова **SQLSetPos**.  
  
 Если выполняется пакет инструкций SQL, количество затронутых строк может быть полный счетчик для всех инструкций в пакете или отдельные счетчики для каждой инструкции в пакете. Дополнительные сведения см. в разделе [пакеты инструкций SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) и [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Число затронутых строк также возвращается SQL_DIAG_ROW_COUNT диагностические поля в заголовке в области диагностики, связанные с дескриптором инструкции. Тем не менее, данные в этом поле сбрасывается после каждой функции вызова на том же дескрипторе инструкции, в то время как значение, возвращаемое функцией **SQLRowCount** остается неизменным до вызова **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, или **SQLSetPos**.
