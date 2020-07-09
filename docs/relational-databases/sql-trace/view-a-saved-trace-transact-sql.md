---
title: Просмотр сохраненной трассировки (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2c89535d15850d528949ae7607f950adb49905b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750871"
---
# <a name="view-a-saved-trace-transact-sql"></a>просмотреть сохраненную трассировку (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе разъясняется, как использовать встроенные функции для просмотра сохраненных трассировок.  
  
### <a name="to-view-a-specific-trace"></a>Просмотр конкретной трассировки  
  
1.  Выполните функцию **fn_trace_getinfo** , указав идентификатор трассировки, сведения о котором необходимо получить. Данная функция возвращает таблицу, в которой перечислены трассировка, свойство трассировки и сведения об этом свойстве.  

     Запустите функцию следующим способом:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a>Просмотр всех существующих трассировок  
  
1.  Выполните функцию **fn_trace_getinfo** , указав значения `0` или `default`. Данная функция возвращает таблицу, в которой перечислены все трассировки, свойства трассировок и сведения об этих свойствах.  
  
     Функция вызывается следующим образом:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a>Безопасность .NET Framework  
 Для выполнения встроенной функции **fn_trace_getinfo**пользователю требуются следующие разрешения:  
  
 ALTER TRACE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [sys.fn_trace_getinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Просмотр и анализ трассировок с помощью приложения SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
