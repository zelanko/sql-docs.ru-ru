---
description: Определение числа затрагиваемых строк
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 14114700c4d79f83f0388509056dd0b49bb21a8d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483077"
---
# <a name="determining-the-number-of-affected-rows"></a>Определение числа затрагиваемых строк
После того как приложение обновляет, удаляет или вставляет строки, оно может вызвать **SQLRowCount** , чтобы определить, сколько строк было затронуто. **SQLRowCount** возвращает это значение, независимо от того, были ли строки обновлены, удалены или вставлены с помощью инструкции **Update**, **Delete**или **INSERT** , выполняя инструкцию позиционированного обновления или удаления или вызывая функцию **SQLSetPos**.  
  
 При выполнении пакета инструкций SQL количество затронутых строк может быть общим счетчиком для всех инструкций в пакете или отдельных счетчиков для каждой инструкции в пакете. Дополнительные сведения см. в разделе [пакеты инструкций SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) и [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Количество затронутых строк также возвращается в поле заголовка диагностики SQL_DIAG_ROW_COUNT в области диагностики, связанной с маркером инструкции. Однако данные в этом поле сбрасываются после каждого вызова функции на одном и том же маркере инструкции, тогда как значение, возвращаемое функцией **SQLRowCount** , остается прежним до вызова **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**или **SQLSetPos**.
