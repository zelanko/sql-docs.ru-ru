---
title: Пакетная обработка вызовов хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b50350006abba5085b11010f26aa88a89b07393f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193994"
---
# <a name="batching-stored-procedure-calls"></a>Создание пакетной обработки вызовов хранимых процедур
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента автоматически создает пакеты вызовов хранимых процедур на сервер, когда это необходимо. Драйвер производит это действие только при использовании управляющей последовательности ODBC CALL и не производит его для инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. Создание пакетов вызовов хранимых процедур может уменьшить количество обменов данных с сервером и значительно повысить производительность.  
  
 Драйвер создает пакеты вызовов процедур на сервере при выполнении пакета, который содержит несколько управляющих последовательностей ODBC CALL. Он также создает пакеты вызовов процедур, когда массивы связанных параметров используются с управляющей последовательностью ODBC CALL. Например, если вы используете либо привязки на уровне строк или параметр для связывания массива из пяти элементов с параметрами инструкции ODBC CALL SQL при **SQLExecute** или **SQLExecDirect** называется, драйвер отправляет один пакет с пятью вызовами процедур на сервер.  
  
## <a name="see-also"></a>См. также  
 [Выполнение хранимых процедур](running-stored-procedures.md)  
  
  
