---
title: MSSQLSERVER_3452 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 775a141774bf8974aa874f7879ce3b65694cf17d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723490"
---
# <a name="mssqlserver_3452"></a>MSSQLSERVER_3452
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
