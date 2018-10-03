---
title: Общие сведения о безопасности (репликация) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3414833d7a188f71a944aace1cea85c1e6fe517b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157253"
---
# <a name="security-overview-replication"></a>Общие сведения о безопасности (репликация)
  Основные принципы обеспечения безопасности среды репликации предполагают четкое понимание параметров проверки подлинности и авторизации, понимание правильного использования возможностей фильтрации репликации, а также знание специальных методов обеспечения безопасности каждого элемента среды репликации. Среда репликации включает распространитель, издатель, подписчики и папку моментальных снимков. Данный раздел посвящен безопасности репликации, но она основана на безопасности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и безопасности Windows. Следовательно, необходимо понимать как эти основы, так и особенности обеспечения безопасности репликации. Дополнительные сведения см. в разделе [Вопросы безопасности при установке SQL Server](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md). Дополнительные сведения о вопросах безопасности публикации Oracle см. в подразделе «Модель безопасности репликации» раздела [Design Considerations and Limitations for Oracle Publishers](../non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Предотвращение угроз и устранение уязвимостей (репликация)](threat-and-vulnerability-mitigation-replication.md)  
 Объясняются потенциальные угрозы топологии репликации и методы снижения этих угроз.  
  
 [Идентификатор и управление доступом (репликация)](identity-and-access-control-replication.md)  
 Объясняются способы использования проверки подлинности, авторизации и фильтрации для обеспечения безопасности топологии репликации.  
  
 [Безопасная разработка (репликация)](secure-development-replication.md)  
 Приводится поведение репликации в условиях защиты, рекомендации по обеспечению безопасности репликации и минимальные разрешения для репликации.  
  
 [Безопасное развертывание (репликация)](secure-deployment-replication.md)  
 Объясняются оптимальные методы защиты топологии репликации.  
  
## <a name="see-also"></a>См. также  
 [Безопасность и защита (репликация)](security-and-protection-replication.md)  
  
  
