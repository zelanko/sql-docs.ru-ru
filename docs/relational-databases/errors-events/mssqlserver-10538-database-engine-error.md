---
title: MSSQLSERVER_10538 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cd67af96f58396c3f10ffbd97c48bfe2f6602211
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68060625"
---
# <a name="mssqlserver_10538"></a>MSSQLSERVER_10538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10538|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_INVALID_PLANGUIDE_HANDLE|  
|Текст сообщения|Не удается найти структуру плана, поскольку указанный идентификатор структуры плана имеет значение NULL или является недопустимым, либо отсутствует разрешение на объект, упоминаемый в структуре плана. Убедитесь, что идентификатор структуры плана является допустимым, текущий сеанс настроен на правильный контекст базы данных и имеется разрешение ALTER DATABASE или разрешение ALTER на объект, упоминаемый в структуре плана.|  
  
## <a name="explanation"></a>Объяснение  
Идентификатор указанной структуры плана имеет значение NULL или является недопустимым, либо отсутствует разрешение на объект, указанный в структуре плана.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что идентификатор структуры плана допустим, текущий сеанс настроен на правильный контекст базы данных и имеется разрешение ALTER DATABASE или разрешение ALTER на объект, упоминаемый в структуре плана.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
