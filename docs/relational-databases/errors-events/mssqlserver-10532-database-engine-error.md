---
title: "MSSQLSERVER_ 10532 | Документация Майкрософт"
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
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e105f17279de3903519435fdc4590431ea716158
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver10532"></a>MSSQLSERVER_10532
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10532|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_ELIGIBLE_STMT|  
|Текст сообщения|Не удается создать структуру плана '%.\*ls', поскольку пакет или модуль, заданный параметром **@plan_handle**, не содержит инструкций, допустимых для структуры плана. Укажите другое значение для параметра **@plan_handle**.|  
  
## <a name="explanation"></a>Объяснение  
Пакет или модуль, заданный параметром **@plan_handle**, не содержит инструкций, допустимых для структуры плана.  
  
## <a name="user-action"></a>Действие пользователя  
Укажите другое значение для параметра **@plan_handle**.  
  
## <a name="see-also"></a>См. также:  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

