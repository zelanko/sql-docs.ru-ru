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
manager: craigg
ms.openlocfilehash: f4764d1299488f5f6089f6a029f7e44a9dd712a3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780712"
---
# <a name="mssqlserver1458"></a>MSSQLSERVER_1458
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
[Мониторинг зеркального отображения базы данных (SQL Server)](~/database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
