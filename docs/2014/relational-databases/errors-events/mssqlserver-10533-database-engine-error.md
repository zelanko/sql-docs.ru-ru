---
title: MSSQLSERVER_10533 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 86bd82dfd095baeacb35f8454859adb938123f52
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48066344"
---
# <a name="mssqlserver10533"></a>MSSQLSERVER_10533
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10533|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NAME_TOO_BIG|  
|Текст сообщения|Не удалось создать структуру плана «%.*ls», поскольку имя структуры плана превышает по длине максимально допустимое значение, равное 124 символам. Укажите имя, содержащее менее 125 символов.|  
  
## <a name="explanation"></a>Объяснение  
 Имя структуры плана превышает по длине максимально допустимое значение, равное 124 символам.  
  
## <a name="user-action"></a>Действие пользователя  
 Укажите имя, содержащее менее 125 символов.  
  
## <a name="see-also"></a>См. также  
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
