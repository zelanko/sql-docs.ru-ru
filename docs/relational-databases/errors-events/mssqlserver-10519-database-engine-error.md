---
description: MSSQLSERVER_10519
title: MSSQLSERVER_10519 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10519 (Database Engine error)
ms.assetid: 3be393a1-b186-41ae-afb9-a3d07ff354bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dbb694019769896c1af7d461a8c549f1fd7df696
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338920"
---
# <a name="mssqlserver_10519"></a>MSSQLSERVER_10519
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10519|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_INCOMPATIBLE_STMT_AND_HINTS|  
|Текст сообщения|Не удается создать структуру плана "%.\*ls", так как указания, заданные в параметре **\@hints**, нельзя применить к инструкции, заданной параметром **\@stmt** или **\@statement_start_offset**. Убедитесь, что заданные указания можно применить к этой инструкции.|  
  
## <a name="explanation"></a>Объяснение  
Указания, заданные в параметре **\@hints**, нельзя применить к инструкции, заданной параметром **\@stmt** или **\@statement_start_offset**.  
  
## <a name="user-action"></a>Действие пользователя  
Задайте указания, которые могут быть применены к этой инструкции.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
