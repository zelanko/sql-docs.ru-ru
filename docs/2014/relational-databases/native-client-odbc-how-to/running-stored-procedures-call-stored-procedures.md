---
title: Вызов хранимых процедур (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a960df20b7b07bffab900589ae4d520541d720c1
ms.sourcegitcommit: 82a1ad732fb31d5fa4368c6270185c3f99827c97
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688667"
---
# <a name="call-stored-procedures-odbc"></a>Вызов хранимых процедур (ODBC)
  Когда инструкция SQL вызывает хранимую процедуру с помощью предложения escape-вызова ODBC, драйвер Microsoft SQL Server отправляет процедуру SQL Server с помощью механизма удаленного вызова хранимой процедуры (RPC). Запросы RPC пропускают большую часть синтаксической проверки и обработки параметров инструкции в SQL Server; они быстрее, чем инструкция Transact-SQL EXECUTE.  
  
 Пример приложения, демонстрирующий эту функцию, см. в разделе [обработка кодов возврата и &#40;выходных&#41;параметров ODBC](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Выполнение процедуры с помощью RPC  
  
1.  Сконструируйте инструкцию SQL, использующую escape-последовательность ODBC CALL. В этой инструкции для каждого входного, входного-выходного и выходного параметров, а также для возвращаемого процедурой значения (при его наличии) используются маркеры параметров.  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Вызовите [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) для каждого параметра входа, входа-выхода и выхода, а также для значения, возвращаемого процедурой (если оно имеется).  
  
3.  Выполните инструкцию с помощью [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Если приложение отправляет процедуру при помощи синтаксиса Transact-SQL EXECUTE (в отличие от escape-последовательности ODBC CALL), драйвер SQL Server ODBC передает этот вызов процедуры SQL Server в виде инструкции SQL, а не RPC. Кроме того, при использовании инструкции Transact-SQL EXECUTE выходные параметры не возвращаются.  
  
## <a name="see-also"></a>См. также статью  
 [Разделы &#40;руководства по запуску хранимых процедур&#41;  ODBC](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
 [Пакетная обработка вызовов хранимых процедур](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Выполнение хранимых процедур](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Вызов хранимой процедуры](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Процедуры](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
