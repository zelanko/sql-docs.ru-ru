---
title: MSSQLSERVER_10531 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10531 (Database Engine error)
ms.assetid: bb40e994-231c-44ce-933f-8d767fb2f450
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1706e67643b2f0c5360399b13a38b5dcec57d9ce
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781464"
---
# <a name="mssqlserver_10531"></a>MSSQLSERVER_10531
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10531|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_ELIGIBLE_STMT|  
|Текст сообщения|Не удалось создать структуру плана «%.*ls» из кэша, поскольку пользователь не имеет необходимых разрешений. Предоставьте разрешение VIEW SERVER STATE пользователю, создающему структуру плана.|  
  
## <a name="explanation"></a>Объяснение  
Пользователь не имеет разрешений, необходимых для создания указанной структуры плана из кэша планов.  
  
## <a name="user-action"></a>Действие пользователя  
Предоставьте разрешение VIEW SERVER STATE пользователю, создающему структуру плана.  
  
## <a name="see-also"></a>См. также:  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
