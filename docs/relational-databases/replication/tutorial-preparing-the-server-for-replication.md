---
title: "Учебник. Подготовка сервера к репликации | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6c935d16aaaeddfed65b6f0af1bf5fb35d609dee
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="tutorial-preparing-the-server-for-replication"></a>Учебник. Подготовка сервера к репликации
Перед тем, как настраивать топологию репликации, важно предусмотреть средства безопасности. В этом учебнике описывается, как лучше обезопасить топологию репликации и как настроить распространение, которое является первым шагом в репликации данных. В первую очередь необходимо пройти именно этот учебник.  
  
> [!NOTE]  
> Чтобы безопасно выполнять репликацию данных между серверами, следует выполнять все рекомендации, приведенные в разделе [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
В этом учебнике описывается, как подготовить сервер для безопасного выполнения репликации с минимальным числом привилегий. На первом занятии создаются учетные записи службы Windows, используемые для запуска агентов репликации. На втором занятии демонстрируется настройка папки, используемой для формирования и хранения моментальных снимков публикации. На третьем занятии выполняется настройка распространения и установка разрешений.  
  
## <a name="requirements"></a>Требования  
Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченный опыт работы с репликацией.  
  
Для работы с этим учебником в системе должны быть установлены следующие компоненты:  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] с базой данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
**Предполагаемое время для выполнения заданий данного учебника: 30 минут.**  
  
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника  
  
-   [Занятие 1. Создание учетных записей Windows для репликации](../../relational-databases/replication/lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [Занятие 2. Подготовка папки моментальных снимков](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md)  
  
-   [Урок 3. Настройка распространения](../../relational-databases/replication/lesson-3-configuring-distribution.md)  
  
[Приступить к изучению](../../relational-databases/replication/lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a>См. также:  
[Настройка распространителя](../../relational-databases/replication/configure-distribution.md)  
[Безопасность и защита (репликация)](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
  
