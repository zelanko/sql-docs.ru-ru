---
title: Записи о статусе (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4afef16137404fcdfd3e1d328642f1d314829538
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301375"
---
# <a name="status-records"></a>Записи состояния
Поля в записях состояния содержат информацию о конкретных ошибках или предупреждениях, возвращенных менеджером драйвера, водителем или источником данных, включая номер ошибки S'Lstate, номер ошибки, диагностическое сообщение, номер столбца и номер строки. Записи о состоянии могут быть созданы только в том случае, если функция возвращается SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA или SQL_STILL_EXECUTING. Полный список полей в записях о состоянии приведен в описании функции [S'LGetDiagField.](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Последовательность записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [атрибуты SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Диагностические сообщения](../../../odbc/reference/develop-app/diagnostic-messages.md)
