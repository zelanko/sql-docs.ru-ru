---
title: MSSQLSERVER_8712 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: db6b162b08fc60a96bda225b1b2118f5644107d2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413763"
---
# <a name="mssqlserver8712"></a>MSSQLSERVER_8712
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8712|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|USEPLAN_ERR_NO_INDEX|  
|Текст сообщения|Индекс «%.*ls», заданный в указании USE PLAN, не существует. Укажите существующий индекс или создайте индекс с указанным именем.|  
  
## <a name="explanation"></a>Объяснение  
 Индекс, заданный в указании USE PLAN, не существует.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что существуют все индексы, которые заданы в указании USE PLAN.  
  
## <a name="see-also"></a>См. также  
 [Указания запросов (Transact-SQL)](/sql/t-sql/queries/hints-transact-sql-query)   
 [Руководства планов](../performance/plan-guides.md)  
  
  
