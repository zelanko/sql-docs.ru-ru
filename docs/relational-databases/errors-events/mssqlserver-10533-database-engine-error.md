---
title: MSSQLSERVER_10533 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dd36f3bee3b11cecc8de10c7a9a6445f1d4ab5c7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781443"
---
# <a name="mssqlserver_10533"></a>MSSQLSERVER_10533
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10533|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NAME_TOO_BIG|  
|Текст сообщения|Не удалось создать структуру плана «%.*ls», поскольку имя структуры плана превышает по длине максимально допустимое значение, равное 124 символам. Укажите имя, содержащее менее 125 символов.|  
  
## <a name="explanation"></a>Объяснение  
Имя структуры плана превышает по длине максимально допустимое значение, равное 124 символам.  
  
## <a name="user-action"></a>Действие пользователя  
Укажите имя, содержащее менее 125 символов.  
  
## <a name="see-also"></a>См. также:  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
