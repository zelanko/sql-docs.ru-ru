---
description: MSSQLSERVER_10538
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
ms.openlocfilehash: b938580c448f0073784e58763d35f4a795317c44
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338200"
---
# <a name="mssqlserver_10538"></a>MSSQLSERVER_10538
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
