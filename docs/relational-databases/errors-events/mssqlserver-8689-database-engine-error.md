---
title: "MSSQLSERVER_8689 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9bde8c78bcece74c17820bb11390c048355e4d5a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8689|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|USEPLAN_ERR_NO_DB|  
|Текст сообщения|База данных "%.*ls", заданная в указании USE PLAN, не существует. Укажите существующую базу данных.|  
  
## <a name="explanation"></a>Объяснение  
База данных, которая задана в указании USE PLAN, не существует.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь в том, что существуют все базы данных, которые заданы в указании USE PLAN.  
  
## <a name="see-also"></a>См. также:  
[Указания запросов (Transact-SQL)](~/t-sql/queries/hints-transact-sql-query.md)  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
  
