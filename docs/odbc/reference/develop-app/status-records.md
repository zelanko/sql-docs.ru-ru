---
title: Состояние записи | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 986cd3c48104bfe822934eb415b854b8e976f242
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149116"
---
# <a name="status-records"></a>Записи состояния
Поля в записях состояния содержат сведения о конкретных ошибках и предупреждениях, возвращаемых источником диспетчера драйверов, драйвер или данных, включая SQLSTATE, номер внутренней ошибки, диагностическое сообщение, номер столбца и номер строки. Состояние записи могут создаваться только в том случае, если функция возвращает значение SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA или SQL_STILL_EXECUTING. Полный список полей в записях состояния, см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Последовательность записей состояния](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [Атрибуты SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Диагностические сообщения](../../../odbc/reference/develop-app/diagnostic-messages.md)
