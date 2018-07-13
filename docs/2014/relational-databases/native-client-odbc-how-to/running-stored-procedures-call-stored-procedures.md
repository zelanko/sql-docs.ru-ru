---
title: Вызов хранимых процедур (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37ce27067c4ad30e38b6d3c168b8f676815b693d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411303"
---
# <a name="call-stored-procedures-odbc"></a>Вызов хранимых процедур (ODBC)
  Когда инструкция SQL вызывает хранимую процедуру при помощи escape-последовательности ESCAPE ODBC CALL, драйвер Microsoft® SQL Server™ отправляет процедуру на SQL Server при помощи механизма удаленного вызова хранимой процедуры. Запросы RPC пропускают большую часть синтаксической проверки и обработки параметров инструкции в SQL Server; они быстрее, чем инструкция Transact-SQL EXECUTE.  
  
 Образец приложения, демонстрирующий эту возможность, см. в разделе [Обработка кодов возврата и выходные параметры &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Выполнение процедуры с помощью RPC  
  
1.  Сконструируйте инструкцию SQL, использующую escape-последовательность ODBC CALL. В этой инструкции для каждого входного, входного-выходного и выходного параметров, а также для возвращаемого процедурой значения (при его наличии) используются маркеры параметров.  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Вызовите [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) для каждого набора входных данных ввода вывода, выходного параметра и для возвращаемого процедурой значения (если таковые имеются).  
  
3.  Выполните инструкцию с [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Если приложение отправляет процедуру при помощи синтаксиса Transact-SQL EXECUTE (в отличие от escape-последовательности ODBC CALL), драйвер SQL Server ODBC передает этот вызов процедуры SQL Server в виде инструкции SQL, а не RPC. Кроме того, при использовании инструкции Transact-SQL EXECUTE выходные параметры не возвращаются.  
  
## <a name="see-also"></a>См. также  
 [Выполнение разделы руководства, посвященные хранимых процедур &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Пакетная обработка вызовов хранимых процедур](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Выполнение хранимых процедур](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Вызов хранимой процедуры](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Процедуры](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
