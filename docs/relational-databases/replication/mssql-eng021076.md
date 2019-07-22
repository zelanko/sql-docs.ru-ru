---
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
ms.openlocfilehash: d12461d68884f5d8764d202f413e9b43e85fda26
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091986"
---
# <a name="mssqleng021076"></a>MSSQL_ENG021076
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
  
  
