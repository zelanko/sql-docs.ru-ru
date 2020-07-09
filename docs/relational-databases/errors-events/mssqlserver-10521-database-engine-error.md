---
title: MSSQLSERVER_10521 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3daa4f6dcfc9be9f34da2be3c1344dd694b811ae
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781479"
---
# <a name="mssqlserver_10521"></a>MSSQLSERVER_10521
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10521|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_PARAM_NEEDED|  
|Текст сообщения|Не удалось создать структуру плана "%.\*ls", поскольку значение **\@type** указано как "%ls", а параметр "%ls" имеет значение NULL. Этот тип должен иметь значение, отличное от NULL, для этого параметра. Укажите для этого параметра значение, отличное от NULL, либо измените его тип таким образом, чтобы он допускал значение NULL.|  
  
## <a name="explanation"></a>Объяснение  
В параметре **\@type** указан тип, требующий отличное от NULL значение для указанного параметра, но было задано значение NULL.  
  
## <a name="user-action"></a>Действие пользователя  
Укажите для этого параметра значение, отличное от NULL, либо измените его тип таким образом, чтобы он допускал значение NULL.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
