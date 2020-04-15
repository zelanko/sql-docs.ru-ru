---
title: Пакетирование Сохраненные Процедуры Вызовы (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ef16b6c6b599274072bddfc49a58de2a10712ea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304570"
---
# <a name="batching-stored-procedure-calls"></a>Создание пакетной обработки вызовов хранимых процедур
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC автоматически при необходимости при необходимости отыскивает сохраненные процедурные вызовы на сервер. Драйвер производит это действие только при использовании управляющей последовательности ODBC CALL и не производит его для инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE. Создание пакетов вызовов хранимых процедур может уменьшить количество обменов данных с сервером и значительно повысить производительность.  
  
 Драйвер создает пакеты вызовов процедур на сервере при выполнении пакета, который содержит несколько управляющих последовательностей ODBC CALL. Он также создает пакеты вызовов процедур, когда массивы связанных параметров используются с управляющей последовательностью ODBC CALL. Например, если вы используете привязку параметра, имеющего ряд строки или столбец, для привязки массива с пятью элементами к параметрам оператора ODBC CALL S-L, при вызове **S'LExecute** или **S'LExecDirect,** водитель отправляет на сервер одну партию с пятью процедурными вызовами.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение хранимых процедур](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
