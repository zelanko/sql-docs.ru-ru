---
title: MSSQLSERVER_3452 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d18f58019354e6516403fdad3e2a676b5ed6d018
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551569"
---
# <a name="mssqlserver_3452"></a>MSSQLSERVER_3452
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3452|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REC_CHECKIDENTITY|  
|Текст сообщения|Процедура восстановления базы данных «%.*ls» (%d) обнаружила возможное несовпадение тождественных значений в таблице со значением идентификатора %d. Запустите процедуру DBCC CHECKIDENT ("%.\*ls").|  
  
## <a name="explanation"></a>Объяснение  
 Во время обновления сервера до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] процесс восстановления значений идентификаторов в базе данных обнаружил несогласованность в метаданных.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполнить команду DBCC CHECKIDENT.  
  
  
