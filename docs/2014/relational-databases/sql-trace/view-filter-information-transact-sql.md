---
title: Просмотр сведений о фильтрах (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: abeeac1dc2c6d06a0b1ce89f4dff35415f7189fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63285616"
---
# <a name="view-filter-information-transact-sql"></a>просмотреть сведения фильтров (Transact-SQL)
  Подраздел описывает использование встроенных функций для просмотра сведений фильтра трассировки.  
  
### <a name="to-view-filter-information"></a>Просмотр сведений о фильтре  
  
1.  Выполните функцию **fn_trace_getfilterinfo** , указав идентификатор трассировки, для которой требуются сведения о фильтре. Эта функция возвращает таблицу, в которой перечислены фильтры, столбцы, к которым применяются фильтры, и значения для фильтрования.  
  
     Запустите функцию следующим способом:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a>См. также  
 [sys.fn_trace_getfilterinfo (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)   
 [Системные хранимые процедуры (Transact-SQL)](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Хранимые процедуры приложения SQL Server Profiler (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
