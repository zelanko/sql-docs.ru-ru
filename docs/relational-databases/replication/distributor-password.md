---
title: "Пароль распространителя | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
caps.latest.revision: "24"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25add00605312f2a290f265088f59f763410df13
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="distributor-password"></a>Пароль распространителя
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Если на странице **Издатели** этого мастера пользователь включил одного или нескольких издателей для использования данного сервера в качестве удаленного распространителя, нужно задать пароль для соединения, устанавливаемого репликацией, между издателем и удаленным распространителем, используя имя входа **distributor_admin**. Тот же пароль необходимо ввести для каждого издателя, использующего этот удаленный распространитель, на странице **Административный пароль** мастера создания публикаций или мастера настройки распространения. Дополнительные сведения о безопасности распространителей см. в разделе [Защита распространителя](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="options"></a>Параметры  
 **Пароль**  
 Введите надежный пароль для соединения между издателем и удаленным распространителем.  
  
 **Подтвердите пароль**  
 Повторно введите пароль, чтобы подтвердить правильность ввода.  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
