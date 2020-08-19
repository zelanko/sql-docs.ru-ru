---
description: Диагностика
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 918dce41ca1c7e7b43c1a6d25de2c75a83312715
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476716"
---
# <a name="diagnostics"></a>Диагностика
Функции в ODBC возвращают диагностические данные двумя способами. Код возврата указывает на общее успешное или неуспешное выполнение функции, в то время как диагностические записи предоставляют подробные сведения о функции. По крайней мере одна диагностическая запись — возвращается запись заголовка, даже если функция выполнена.  
  
 Диагностические сведения используются во время разработки для перехвата ошибок программирования, таких как недопустимые дескрипторы и синтаксические ошибки, в жестко запрограммированных инструкциях SQL. Он используется во время выполнения для перехвата ошибок во время выполнения и предупреждений, таких как усечение данных, нарушения прав доступа и синтаксические ошибки в инструкциях SQL, вводимых пользователем.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Коды возврата](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Диагностические записи](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Использование SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Реализация SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Примеры диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
