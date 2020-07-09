---
title: MSSQLSERVER_10537 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0121d16fd25659a40b9c7a05df154028227d8745
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781404"
---
# <a name="mssqlserver_10537"></a>MSSQLSERVER_10537
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
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
  
