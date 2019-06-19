---
title: MSSQLSERVER_10507 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ea11cc0403c9a417437c7b92d0eec5c46bcffb69
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048402"
---
# <a name="mssqlserver10507"></a>MSSQLSERVER_10507
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10507|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_STMT_DOES_NOT_MATCH|  
|Текст сообщения|Не удалось создать структуру плана "%.\*ls", поскольку инструкция, указанная параметрами **@stmt** и **@module_or_batch** или параметрами **@plan_handle** и **@statement_start_offset** , не соответствует ни одной инструкции в указанном модуле или пакете. Измените значения параметров таким образом, чтобы они соответствовали инструкции в модуле или пакете.|  
  
## <a name="explanation"></a>Объяснение  
Инструкция в указанном модуле или пакете не соответствует указанной инструкцией или с величиной смещения инструкции.  
  
## <a name="user-action"></a>Действие пользователя  
Измените указанные значения параметров, чтобы они соответствовали инструкции в модуле или пакете.  
  
## <a name="see-also"></a>См. также:  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
