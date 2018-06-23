---
title: MSSQLSERVER_1458 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8ff43b96cfe4e520972b9293d9843417b63e1683
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190011"
---
# <a name="mssqlserver1458"></a>MSSQLSERVER_1458
    
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
  
## <a name="see-also"></a>См. также  
 [Мониторинг зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  