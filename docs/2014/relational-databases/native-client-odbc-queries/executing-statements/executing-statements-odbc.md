---
title: Выполненные инструкции (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: rothja
ms.author: jroth
ms.openlocfilehash: 01dc4298855fd3418029164dea3ed089185da934
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85018424"
---
# <a name="executing-statements-odbc"></a>Выполнение инструкций (ODBC)
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Драйвер ODBC для собственного клиента предоставляет различные способы выполнения инструкций SQL в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базе данных:  
  
-   прямое выполнение;  
  
-   подготовленное выполнение.  
  
 Прямое выполнение включает в себя создание символьной строки [!INCLUDE[tsql](../../../includes/tsql-md.md)] , содержащей инструкцию, и ее отправка для выполнения с помощью функции **SQLExecDirect** . Подготовленное выполнение включает в себя построение строки символов, содержащей инструкцию [!INCLUDE[tsql](../../../includes/tsql-md.md)], и последующее выполнение этой инструкции в два шага. На первом этапе функция [SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) используется для синтаксического анализа и компиляции плана выполнения инструкции в [!INCLUDE[ssDE](../../../includes/ssde-md.md)] . На втором этапе используется функция **SQLExecute** для выполнения ранее подготовленного плана выполнения. Это снижает расход ресурсов на синтаксический анализ и компиляцию при каждом выполнении. Подготовленное выполнение часто используется приложениями для многократного выполнения параметризованных инструкций SQL.  
  
 Как при непосредственном, так и при подготовленном выполнении может выполняться одиночная инструкция [!INCLUDE[tsql](../../../includes/tsql-md.md)] или пакет инструкций SQL, может также вызываться хранимая процедура.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Прямое выполнение](direct-execution.md)  
  
-   [Подготовленное выполнение](prepared-execution.md)  
  
-   [Процедуры](procedures.md)  
  
-   [Пакеты инструкций](batches-of-statements.md)  
  
-   [Действие параметров ISO](effects-of-iso-options.md)  
  
## <a name="see-also"></a>См. также:  
 [Выполняя запросы &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  
