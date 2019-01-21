---
title: MSSQL_ENG021075 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dd28038ac1230ecd584c0cacefe751e006a9f8a4
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54132814"
---
# <a name="mssqleng021075"></a>MSSQL_ENG021075
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21075|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Исходный моментальный снимок публикации "%s" еще недоступен.|  
  
## <a name="explanation"></a>Объяснение  
 Ошибка MSSQL_ENG021075 возникает, если агент распространителя или агент слияния запускается до окончания создания моментального снимка агентом моментальных снимков.  
  
## <a name="user-action"></a>Действие пользователя  
 Если со времени создания подписки агент моментальных снимков для публикации не запускался или если он не запускался со времени последней повторной инициализации подписки, запустите агент моментальных снимков и позвольте ему полностью завершить свою работу до запуска агента распространителя или агента слияния. Дополнительные сведения см. в статье [Создание и применение моментального снимка](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
 Если агент моментальных снимков не завершил свою работу, проверьте журнал агента моментальных снимков на наличие ошибок и устраните эти ошибки. Сведения о просмотре состояния агента и сведений об ошибках в мониторе репликации см. в статье [Просмотр сведений и выполнение задач с помощью монитора репликации](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
 Если ошибка продолжает возникать, увеличьте протоколирование агента и укажите выходной файл для журнала. В зависимости от контекста ошибки эта мера может помочь в определении шагов, которые привели к ошибке или появлению дополнительных сообщений об ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
