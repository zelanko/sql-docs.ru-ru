---
title: MSSQLSERVER_10539 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10539 (Database Engine error)
ms.assetid: 49c26ff7-18b8-4f07-a087-f45f63463b3b
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d8b34796716388fbdaacc83907aedd1683959290
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426283"
---
# <a name="mssqlserver10539"></a>MSSQLSERVER_10539
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10539|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_PLAN_FOR_STMT|  
|Текст сообщения|Не удается создать структуру плана «%.*ls» из кэша, поскольку план запроса для инструкции с начальным смещением %d недоступен. Эта ошибка может произойти, если инструкция зависит от объектов базы данных, которые еще не были созданы. Убедитесь, что существуют все необходимые объекты базы данных, и выполните инструкцию перед созданием структуры плана.|  
  
## <a name="explanation"></a>Объяснение  
 В кэше планов недоступен план запроса для инструкции с указанным начальным смещением.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что существуют все необходимые объекты базы данных, и выполните инструкцию перед созданием структуры плана.  
  
## <a name="see-also"></a>См. также  
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
