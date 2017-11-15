---
title: "MSSQLSERVER_125 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: "125"
helpviewer_keywords: 125 (Database Engine error)
ms.assetid: 0f58338d-2ea0-48b8-8a20-c438b0940433
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 490c1814d82718080864427ceca229494390607e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver125"></a>MSSQLSERVER_125
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|125|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|Выражения Case могут быть вложены только до уровня %d.|  
  
## <a name="explanation"></a>Объяснение  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] допускает применение в выражениях CASE не более 10 уровней вложенности.  
  
## <a name="user-action"></a>Действие пользователя  
Ограничьте уровень вложенности выражений CASE до 10.  
  
## <a name="see-also"></a>См. также:  
[CASE (Transact-SQL)](~/t-sql/language-elements/case-transact-sql.md)  
  
