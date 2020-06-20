---
title: Пакетирование вызовов хранимых процедур | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a0df58ce59853ee15b863cbc7bce34041c37fee4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039507"
---
# <a name="batching-stored-procedure-calls"></a>Создание пакетной обработки вызовов хранимых процедур
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Драйвер ODBC для собственного клиента автоматически выполняет пакетные вызовы хранимых процедур на сервере, если это уместно. Драйвер производит это действие только при использовании управляющей последовательности ODBC CALL и не производит его для инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. Создание пакетов вызовов хранимых процедур может уменьшить количество обменов данных с сервером и значительно повысить производительность.  
  
 Драйвер создает пакеты вызовов процедур на сервере при выполнении пакета, который содержит несколько управляющих последовательностей ODBC CALL. Он также создает пакеты вызовов процедур, когда массивы связанных параметров используются с управляющей последовательностью ODBC CALL. Например, если для привязки массива с пятью элементами к параметрам инструкции SQL CALL, то при вызове **SQLExecute** или **SQLExecDirect** драйвер отправляет один пакет с пятью вызовами процедур на сервер, при использовании привязки параметра на уровне строк или на уровне столбца.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение хранимых процедур](running-stored-procedures.md)  
  
  
