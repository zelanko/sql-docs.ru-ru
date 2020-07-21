---
title: MSSQLSERVER_10535 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 68070291c5e7f50d423b74338dc1f6baeb9c6dfa
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554119"
---
# <a name="mssqlserver_10535"></a>MSSQLSERVER_10535
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10535|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_PLAN|  
|Текст сообщения|Не удается создать структуру плана «%.*ls», поскольку план не найден в кэше планов, соответствующем указанному дескриптору плана. Укажите дескриптор плана в кэше. Список дескрипторов планов, находящихся в кэше, можно получить с помощью запроса к динамическому административному представлению sys.dm_exec_query_stats.|  
  
## <a name="explanation"></a>Объяснение  
 План не был найден в кэше планов, который соответствует указанному дескриптору плана.  
  
## <a name="user-action"></a>Действие пользователя  
 Укажите дескриптор плана в кэше. Список дескрипторов планов, находящихся в кэше, можно получить с помощью запроса к динамическому административному представлению sys.dm_exec_query_stats.  
  
## <a name="see-also"></a>См. также:  
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)   
 [sys.dm_exec_query_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
