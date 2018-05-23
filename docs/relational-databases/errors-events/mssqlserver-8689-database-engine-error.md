---
title: MSSQLSERVER_8689 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2011d72a8d58e6c3c21f8fe746eb8c5b901ccb8d
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
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
  
