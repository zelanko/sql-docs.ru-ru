---
title: Просмотр сведений о фильтрах (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fa38ab23b96bcde8046a4607442b67110cd2d2a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36110120"
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
  
  
