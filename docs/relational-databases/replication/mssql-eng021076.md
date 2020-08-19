---
description: MSSQL_ENG021076
title: MSSQL_ENG021076 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 83ce287264f6ea22fbea94a7bea7416d8935dc4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88378740"
---
# <a name="mssql_eng021076"></a>MSSQL_ENG021076
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21076|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Исходный моментальный снимок для статьи "%s" еще не доступен.|  
  
## <a name="explanation"></a>Объяснение  
 Ошибка MSSQL_ENG021076 может возникнуть, если агент распространителя запускается до того, как агент моментальных снимков закончил создание моментального снимка. Эта ошибка возникает, только если публикация содержит единственную статью. Если публикация содержит несколько статей, то вместо описываемой ошибки возникает ошибка MSSQL_ENG021075. Дополнительные сведения см. в разделе [MSSQL_ENG021075](../../relational-databases/replication/mssql-eng021075.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Если агент моментальных снимков для публикации не запускался после создания подписки или если он не запускался с момента повторной инициализации подписки, запустите агент моментальных снимков и дайте ему возможность завершить работу, прежде чем запустить агент распространителя. Дополнительные сведения см. в статье [Создание и применение моментального снимка](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
 Если агент моментальных снимков не завершил свою работу, проверьте журнал агента моментальных снимков на наличие ошибок и устраните эти ошибки. Сведения о просмотре состояния агента и сведений об ошибках в мониторе репликации см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
 Если ошибка продолжает возникать, увеличьте протоколирование агента и укажите выходной файл для журнала. В зависимости от контекста ошибки эта мера может помочь в определении шагов, которые привели к ошибке или появлению дополнительных сообщений об ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
