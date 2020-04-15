---
title: Определение количества затронутых строк (ru) Документы Майкрософт
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
ms.openlocfilehash: 156a5fe41d2c9b57a33bbc2bdb4540d1f5b00340
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305895"
---
# <a name="determining-the-number-of-affected-rows"></a>Определение числа затрагиваемых строк
После обновления приложения, удаления или вставки строк, он может вызвать **S'LRowCount,** чтобы определить, сколько строк было затронуто. **S'LRowCount** возвращает это значение независимо от того, были ли строки обновлены, удалены или вставлены, выполнив **ОБНОВЛЕНИЕ,** **DELETE**, или **заявление INSERT,** выполнив позиционированное обновление или удаление оператора, или позвонив в **S'LSetPos.**  
  
 Если выполняется серия инструкций S'L, количество затронутых строк может быть общим подсчетом для всех инструкций в пакете или индивидуальных подсчетов для каждой выписки в пакете. Для получения дополнительной [информации](../../../odbc/reference/develop-app/batches-of-sql-statements.md) см. [Multiple Results](../../../odbc/reference/develop-app/multiple-results.md)  
  
 Количество затронутых строк также возвращается в поле SQL_DIAG_ROW_COUNT диагностическом заголовке в диагностической области, связанной с ручкой оператора. Тем не менее, данные в этой области сбрасываются после того, как каждый вызов функции на той же ручке оператора, в то время как значение, возвращенное **S'LRowCount** остается неизменным до тех пор, пока не будет вызван вызов в **S'LBulkOperations,** **S'LExecute,** **S'LExecDirect**, **S'LPrepare**, или **S'LSetPos.**
