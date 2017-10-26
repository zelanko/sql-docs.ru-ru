---
title: "Диагностика | Документы Microsoft"
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
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: adb6f66ecfbff558fd163437a56453efb4265185
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="diagnostics"></a>Диагностика
В ODBC возвращают диагностические сведения двумя способами. Код возврата указывает общий успех или сбой функции, а диагностические записи предоставляют подробные сведения о функции. По крайней мере одна диагностическая запись — запись заголовка — возвращается, даже если функция выполняется успешно.  
  
 Диагностические сведения используется во время разработки для перехвата ошибок программирования, например недопустимых дескрипторов и синтаксических ошибок в жестко запрограммированных инструкциях SQL. Используется во время выполнения для перехвата ошибок во время выполнения и предупреждения, такие как усечение данных, нарушения прав доступа и синтаксические ошибки в инструкциях SQL, введенных пользователем.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Коды возврата](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Диагностические записи](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [С помощью SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Реализация SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Примеры обработки диагностики](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)

