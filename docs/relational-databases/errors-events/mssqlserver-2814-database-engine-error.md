---
title: "MSSQLSERVER_2814 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2814 (Database Engine error)
ms.assetid: 22800748-9be9-4511-9428-6b8b40e5bef9
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f2408e7a6e34e903ecd9c24d93db222de69f6398
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver2814"></a>MSSQLSERVER_2814
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2814|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PR_POSSIBLE_INFINITE_RECOMPILE|  
|Текст сообщения|Обнаружена возможная бесконечная перекомпиляция для SQLHANDLE %hs, PlanHandle %hs, от смещения %d до смещения %d. Причиной последней перекомпиляции было %d.|  
  
## <a name="explanation"></a>Объяснение  
Одна или несколько инструкций вызвали перекомпиляцию пакета запросов по крайней мере 50 раз. Необходимо исправить указанную инструкцию, чтобы избежать дальнейшей перекомпиляции.  
  
В следующей таблице приводятся причины перекомпиляции.  
  
|Код причины|Description|  
|---------------|---------------|  
|1|Изменение схемы|  
|2|Изменение статистики|  
|3|Отложенная компиляция|  
|4|Изменение параметра SET|  
|5|Изменение временной таблицы|  
|6|Изменение удаленного набора строк|  
|7|Изменение разрешений FOR BROWSE|  
|8|Изменение среды уведомлений о запросах|  
|9|Изменение секционированного представления|  
|10|Изменение параметров курсора|  
|11|Запрошено OPTION (RECOMPILE)|  
  
## <a name="user-action"></a>Действие пользователя  
  
1.  Просмотрите инструкцию, вызывающую перекомпиляцию, запустив следующий запрос. Замените заполнители *sql_handle*, *starting_offset*, *ending_offset* и *plan_handle* соответствующими значениями, указанными в сообщении об ошибке. Обратите внимание, что столбцы **database_name** и **object_name** будут пустыми для динамических и подготовленных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
    SELECT DB_NAME(st.dbid) AS database_name  
  
    , OBJECT_NAME(st.objectid) AS object_name  
  
    , st.text  
  
    FROM sys.dm_exec_query_stats AS qs  
  
    CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st  
  
    WHERE qs.statement_start_offset = *starting_offset*  
  
    AND qs.statement_end_offset = *ending_offset*  
  
    AND qs.plan_handle = *plan_handle*;  
  
2.  В зависимости от описания кода причины измените инструкцию, пакет или процедуру, чтобы избежать перекомпиляции. Например, хранимая процедура может содержать одну или несколько инструкций SET. Эти инструкции должны быть удалены из процедуры. Дополнительные примеры причин повторной компиляции и способов их устранения можно найти в статье [Компиляция пакета, повторная компиляция и проблемы кэширования плана в SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=69175).  
  
3.  Если ошибка повторится, обратитесь в службу поддержки пользователей Майкрософт.  
  
## <a name="see-also"></a>См. также:  
[Класс событий SQL:StmtRecompile](../Topic/SQL:StmtRecompile%20Event%20Class.md)  
  

