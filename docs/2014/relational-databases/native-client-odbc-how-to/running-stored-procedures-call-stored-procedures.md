---
title: Вызов хранимых процедур (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0846567d803eadf4364159fc01fdb8a7853e8a4f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101545"
---
# <a name="call-stored-procedures-odbc"></a>Вызов хранимых процедур (ODBC)
  Когда инструкция SQL вызывает хранимую процедуру при помощи escape-последовательности ESCAPE ODBC CALL, драйвер Microsoft® SQL Server™ отправляет процедуру на SQL Server при помощи механизма удаленного вызова хранимой процедуры. Запросы RPC пропускают большую часть синтаксической проверки и обработки параметров инструкции в SQL Server; они быстрее, чем инструкция Transact-SQL EXECUTE.  
  
 Образец приложения, демонстрирующий эту функцию, в разделе [процесса коды возврата и выходные параметры &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Выполнение процедуры с помощью RPC  
  
1.  Сконструируйте инструкцию SQL, использующую escape-последовательность ODBC CALL. В этой инструкции для каждого входного, входного-выходного и выходного параметров, а также для возвращаемого процедурой значения (при его наличии) используются маркеры параметров.  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Вызовите [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) для каждого входного потока ввода вывода и выходного параметра и для возвращаемого процедурой значения (если таковые имеются).  
  
3.  Выполните инструкцию с [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Если приложение отправляет процедуру при помощи синтаксиса Transact-SQL EXECUTE (в отличие от escape-последовательности ODBC CALL), драйвер SQL Server ODBC передает этот вызов процедуры SQL Server в виде инструкции SQL, а не RPC. Кроме того, при использовании инструкции Transact-SQL EXECUTE выходные параметры не возвращаются.  
  
## <a name="see-also"></a>См. также  
 [Выполнение хранимых процедур инструкции &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Пакетная обработка вызовов хранимых процедур](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Выполнение хранимых процедур](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Вызов хранимой процедуры](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Процедуры](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  