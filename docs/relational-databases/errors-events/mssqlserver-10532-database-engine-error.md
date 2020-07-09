---
title: MSSQLSERVER_ 10532 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adf10542f09e4515020b46d7843e773e5995ca33
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781453"
---
# <a name="mssqlserver_10532"></a>MSSQLSERVER_10532
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10532|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_ELIGIBLE_STMT|  
|Текст сообщения|Не удалось создать структуру плана "%.\*ls", так как пакет или модуль, указанный в **\@plan_handle**, не содержит инструкцию, применимую для структуры плана. Укажите другое значение для параметра **\@plan_handle**.|  
  
## <a name="explanation"></a>Объяснение  
Пакет или модуль, указанный в **\@plan_handle**, не содержит инструкцию, подходящую для структуры плана.  
  
## <a name="user-action"></a>Действие пользователя  
Укажите другое значение для параметра **\@plan_handle**.  
  
## <a name="see-also"></a>См. также:  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
