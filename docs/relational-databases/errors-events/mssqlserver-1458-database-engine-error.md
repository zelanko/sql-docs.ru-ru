---
title: MSSQLSERVER_1458 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 24d5ea772aa3bc698a3bcc60dcc07e38eb23ed92
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781019"
---
# <a name="mssqlserver_1458"></a>MSSQLSERVER_1458
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|1458|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_FAILREDO_ON_PRIMARY|  
|Текст сообщения|В основной копии базы данных «%.*ls» обнаружена ошибка %d, состояние %d, серьезность %d. Зеркальное отображение базы данных приостановлено. Попробуйте устранить причины ошибки и возобновите зеркальное отображение.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение указывает, что в основной базе данных произошла ошибка, вызвавшая временную приостановку зеркального отображения базы данных.  
  
## <a name="user-action"></a>Действие пользователя  
В большинстве случаев ошибка устраняется без вмешательства пользователя. Если проблема будет повторяться, то рекомендуется перезапустить базу данных или экземпляр сервера. Дополнительные сведения см. в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на всех участниках, где произошла ошибка, предшествующая сообщению.  
  
## <a name="see-also"></a>См. также:  
[Наблюдение за зеркальным отображением базы данных (SQL Server)](~/database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
