---
title: "MSSQLSERVER_10539 | Документация Майкрософт"
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
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5d54a85fe2f839e2339234b790acda4e1df0c549
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver10539"></a>MSSQLSERVER_10539
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10539|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_PLAN_FOR_STMT|  
|Текст сообщения|Не удается создать структуру плана «%.*ls» из кэша, поскольку план запроса для инструкции с начальным смещением %d недоступен. Эта ошибка может произойти, если инструкция зависит от объектов базы данных, которые еще не были созданы. Убедитесь, что существуют все необходимые объекты базы данных, и выполните инструкцию перед созданием структуры плана.|  
  
## <a name="explanation"></a>Объяснение  
В кэше планов недоступен план запроса для инструкции с указанным начальным смещением.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что существуют все необходимые объекты базы данных, и выполните инструкцию перед созданием структуры плана.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

