---
title: Диагностика Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a09f46d3fd6aa2f9b9c7310af6d3ddc90f78389f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305155"
---
# <a name="diagnostics"></a>Диагностика
Функции в ODBC возвращают диагностическую информацию двумя способами. Код возврата указывает на общий успех или сбой функции, в то время как диагностические записи предоставляют подробную информацию о функции. По крайней мере одна диагностическая запись - запись заголовка - возвращается, даже если функция успешно.  
  
 Диагностическая информация используется во время разработки для ловли ошибок программирования, таких как недействительные ручки и ошибки синтаксиса в жестко закодированных заявлениях S'L. Он используется во время выполнения для выявления ошибок и предупреждений о времени выполнения, таких как усечение данных, нарушения доступа и ошибки синтаксиса в инструкциях S'L, введенных пользователем.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Коды возврата](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Диагностические записи](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Использование SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Реализация SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Примеры диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
