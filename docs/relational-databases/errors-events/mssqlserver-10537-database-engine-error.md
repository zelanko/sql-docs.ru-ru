---
title: MSSQLSERVER_10537 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df5d659e27b936922dccd90a1bb5ae4ddab3c4c6
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver10537"></a>MSSQLSERVER_10537
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10537|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_DUP_ENABLED|  
|Текст сообщения|Не удается включить структуру плана '%.*ls', поскольку включенная структура плана '%.\*ls' содержит ту же область и то же значение начального смещения для инструкции. Отключите существующую структуру плана перед включением указанной структуры.|  
  
## <a name="explanation"></a>Объяснение  
Существующая структура плана содержит ту же область и то же значение начального смещения, что и инструкция в указанной структуре плана.  
  
## <a name="user-action"></a>Действие пользователя  
Отключите существующую структуру плана перед включением указанной структуры.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Руководства планов](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
