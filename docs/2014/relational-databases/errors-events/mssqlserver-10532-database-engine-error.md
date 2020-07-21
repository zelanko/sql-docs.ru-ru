---
title: MSSQLSERVER_ 10532 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10532 (Database Engine error)
ms.assetid: 01da29ee-bf67-433f-8148-587a7e8d1d76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c92e077135491a87687fbb765affc4642e064ea
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86554149"
---
# <a name="mssqlserver_10532"></a>MSSQLSERVER_10532
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10532|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_NO_ELIGIBLE_STMT|  
|Текст сообщения|Не удается создать структуру плана '%.\*ls', поскольку пакет или модуль, заданный параметром `@plan_handle`, не содержит инструкций, допустимых для структуры плана. Укажите другое значение для параметра `@plan_handle`.|  
  
## <a name="explanation"></a>Объяснение  
 Пакет или модуль, указанный в `@plan_handle`, не содержит инструкцию, подходящую для структуры плана.  
  
## <a name="user-action"></a>Действие пользователя  
 Укажите другое значение для параметра `@plan_handle`.  
  
## <a name="see-also"></a>См. также:  
 [Структуры планов](../performance/plan-guides.md)   
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
