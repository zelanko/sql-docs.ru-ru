---
title: MSSQLSERVER_10507 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 810419dede861e7447bfda9d50aea22ce8b2cf53
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552389"
---
# <a name="mssqlserver_10507"></a>MSSQLSERVER_10507
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10507|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_STMT_DOES_NOT_MATCH|  
|Текст сообщения|Не удалось создать структуру плана "%.\*ls", поскольку инструкция, указанная параметрами `@stmt` и `@module_or_batch` или параметрами `@plan_handle` и `@statement_start_offset`, не соответствует ни одной инструкции в указанном модуле или пакете. Измените значения параметров таким образом, чтобы они соответствовали инструкции в модуле или пакете.|  
  
## <a name="explanation"></a>Объяснение  
 Инструкция в указанном модуле или пакете не соответствует указанной инструкцией или с величиной смещения инструкции.  
  
## <a name="user-action"></a>Действие пользователя  
 Измените указанные значения параметров, чтобы они соответствовали инструкции в модуле или пакете.  
  
## <a name="see-also"></a>См. также:  
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
