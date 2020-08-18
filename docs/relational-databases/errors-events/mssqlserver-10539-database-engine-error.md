---
description: MSSQLSERVER_10539
title: MSSQLSERVER_10539 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f1f36f5b8721a94b7badb3316f30f9b3d4e059d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338210"
---
# <a name="mssqlserver_10539"></a>MSSQLSERVER_10539
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|10539|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_PLAN_FOR_STMT|  
|Текст сообщения|Не удается создать структуру плана «%.*ls» из кэша, поскольку план запроса для инструкции с начальным смещением %d недоступен. Эта ошибка может произойти, если инструкция зависит от объектов базы данных, которые еще не были созданы. Убедитесь, что существуют все необходимые объекты базы данных, и выполните инструкцию перед созданием структуры плана.|  
  
## <a name="explanation"></a>Объяснение  
В кэше планов недоступен план запроса для инструкции с указанным начальным смещением.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что существуют все необходимые объекты базы данных, и выполните инструкцию перед созданием структуры плана.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
