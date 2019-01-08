---
title: Диагностика | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72e79d377371277720e2fcc15a31ce715693d832
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52512090"
---
# <a name="diagnostics"></a>Диагностика
В ODBC возвращают диагностические сведения двумя способами. Код возврата указывает общий успех или сбой функции, а диагностические записи предоставляют подробные сведения о функции. По крайней мере одна диагностическая запись - запись заголовка — возвращается, даже если функция выполняется успешно.  
  
 Диагностические сведения используется во время разработки для перехвата ошибок программирования, например недопустимых дескрипторов и синтаксических ошибок в жестко запрограммированных инструкциях SQL. Используется во время выполнения для перехвата ошибок времени выполнения и предупреждения, такие как усечение данных, нарушения прав доступа и синтаксических ошибок в инструкциях SQL, введенный пользователем.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Коды возврата](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Диагностические записи](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Использование SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Реализация SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Примеры диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
