---
title: "Общие сведения о безопасности (репликация) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d459a80eb15947743a846ce64cfe0013f718320d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="security-overview-replication"></a>Общие сведения о безопасности (репликация)
  Основные принципы обеспечения безопасности среды репликации предполагают четкое понимание параметров проверки подлинности и авторизации, понимание правильного использования возможностей фильтрации репликации, а также знание специальных методов обеспечения безопасности каждого элемента среды репликации. Среда репликации включает распространитель, издатель, подписчики и папку моментальных снимков. Данный раздел посвящен безопасности репликации, но она основана на безопасности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и безопасности Windows. Следовательно, необходимо понимать как эти основы, так и особенности обеспечения безопасности репликации. Дополнительные сведения см. в разделе [Вопросы безопасности при установке SQL Server](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md). Дополнительные сведения о вопросах безопасности публикации Oracle см. в подразделе «Модель безопасности репликации» раздела [Design Considerations and Limitations for Oracle Publishers](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Предотвращение угроз и устранение уязвимостей (репликация)](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
 Объясняются потенциальные угрозы топологии репликации и методы снижения этих угроз.  
  
 [Идентификатор и управление доступом (репликация)](../../../relational-databases/replication/security/identity-and-access-control-replication.md)  
 Объясняются способы использования проверки подлинности, авторизации и фильтрации для обеспечения безопасности топологии репликации.  
  
 [Безопасная разработка (репликация)](../../../relational-databases/replication/security/secure-development-replication.md)  
 Приводится поведение репликации в условиях защиты, рекомендации по обеспечению безопасности репликации и минимальные разрешения для репликации.  
  
 [Безопасное развертывание (репликация)](../../../relational-databases/replication/security/secure-deployment-replication.md)  
 Объясняются оптимальные методы защиты топологии репликации.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность и защита (репликация)](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  

