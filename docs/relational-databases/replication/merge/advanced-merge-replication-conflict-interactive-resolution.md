---
title: Интерактивное разрешение конфликтов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interactive conflict resolution [SQL Server replication]
- interactive resolver [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d6e08fc5617d475196b6ce635f256348f92b0a5e
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352106"
---
# <a name="advanced-merge-replication-conflict---interactive-resolution"></a>Конфликт расширенной репликации слиянием: интерактивное разрешение
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Репликация[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует интерактивный арбитр конфликтов, который позволяет разрешать конфликты вручную при проведении синхронизации по требованию в диспетчере синхронизации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Активируемый во время запуска интерактивный сопо является графическим интерфейсом, отображающим данные для каждой конфликтующей строки. Он обеспечивает возможности просмотра и изменения конфликтующих данных, а также разрешения каждого конфликта по отдельности.  
  
 Интерактивный сопоставитель напоминает средство просмотра конфликтов. Однако в то время как средство просмотра конфликтов отображает результаты уже разрешенных конфликтов после синхронизации слиянием, интерактивный сопоставитель отображает каждый конфликт до его разрешения, что позволяет определить исход каждого конфликта во время синхронизации слиянием. Необходим сотрудник, следящий за интерактивным сопоставителем при возникновении конфликта.  
  
> [!NOTE]  
>  Для работы интерактивного механизма разрешения конфликтов необходим диспетчер синхронизации Windows. Если синхронизация выполняется не диспетчером синхронизации Windows (как синхронизация по расписанию или по запросу в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или мониторе репликации), конфликты устраняются автоматически без вмешательства пользователя в соответствии с сопоставителем, указанным для статьи. Конфликты, затрагивающие логические записи, не отображаются в интерактивном сопоставителе. Для просмотра сведений о таких конфликтах используются хранимые процедуры репликации. Дополнительные сведения см. в статье [Просмотр сведений о конфликтах для публикаций слиянием (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/view-conflict-information-for-merge-publications.md).  
  
## <a name="article-resolvers-and-the-interactive-resolver"></a>Сопоставители статей и интерактивный сопоставитель  
 Сопоставители конфликтов (сопоставитель по умолчанию, обработчик бизнес-логики или пользовательский сопоставитель) назначаются конкретным статьям при создании публикации и следуют определенным правилам при определении набора данных, которые нужно использовать при вводе данных конфликтующих строк. Интерактивный сопоставитель не является автономным сопоставителем конфликтов, использующим правила определения «победителей» и «проигравших», а представляет собой средство, используемое совместно со стандартными (заданными по умолчанию) и пользовательскими сопоставителями конфликтов. Как и прежде, сопоставитель статей определяет «победившую» и «проигравшую» строку, однако при этом интерактивный сопоставитель позволяет пользователю принимать, отклонять или изменять результаты.  
  
 Чтобы использовать интерактивный сопоставитель, необходимо активировать его для каждой статьи и подписки, которая в нем нуждается. После активации для одной или нескольких статей и подписок интерактивный сопоставитель используется при обнаружении конфликта во время синхронизации слиянием.  
  
 Чтобы использовать интерактивный сопоставитель, изучите статьи [Указание интерактивного устранения конфликтов для статей публикации слиянием](../../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md) и [Синхронизация подписки с помощью диспетчера синхронизации Windows (диспетчер синхронизации Windows)](../../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
## <a name="see-also"></a>См. также:  
 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
