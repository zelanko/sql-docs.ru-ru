---
title: "MSSQLSERVER_3452 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 52865b3a6a4a036acafffa97cff5d0fbc6abbbf9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3452|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REC_CHECKIDENTITY|  
|Текст сообщения|Процедура восстановления базы данных «%.*ls» (%d) обнаружила возможное несовпадение тождественных значений в таблице со значением идентификатора %d. Запустите процедуру DBCC CHECKIDENT ("%.\*ls").|  
  
## <a name="explanation"></a>Объяснение  
Во время обновления сервера до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] процесс восстановления значений идентификаторов в базе данных обнаружил несогласованность в метаданных.  
  
## <a name="user-action"></a>Действие пользователя  
Выполнить команду DBCC CHECKIDENT.  
  
