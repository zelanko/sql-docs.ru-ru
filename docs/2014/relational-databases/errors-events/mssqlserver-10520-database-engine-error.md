---
title: MSSQLSERVER_10520 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b8bdf080703fa6bd02fc34b8c31f59407814b93
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968164"
---
# <a name="mssqlserver_10520"></a>MSSQLSERVER_10520
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10520|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_PARAM_NOT_ALLOWED|  
|Текст сообщения|Не удается создать структуру плана '%.*ls', поскольку для параметра @type указано значение '%!s', а для параметра '%!s' указано значение, отличное от NULL. Для заданного типа этот параметр должен иметь значение NULL. Укажите для этого параметра значение NULL либо измените его тип таким образом, чтобы он допускал значение, отличное от NULL.|  
  
## <a name="explanation"></a>Объяснение  
 Для типа, указанного в @type, требуется значение NULL, но предоставлено значение, отличное от NULL.  
  
## <a name="user-action"></a>Действие пользователя  
 Укажите для этого параметра значение NULL либо измените его тип таким образом, чтобы он допускал значение, отличное от NULL.  
  
## <a name="see-also"></a>См. также:  
 [sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Руководства планов](../performance/plan-guides.md)  
  
  
