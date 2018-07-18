---
title: Свойства публикации, страница "Безопасность агентов" | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.agentsecurity.f1
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c4b3c16d6baad3acd6fe3e9c2ff5c9b9e6d6fd16
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352026"
---
# <a name="publication-properties-agent-security"></a>Свойства публикации, агент безопасности
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Страница **Безопасность агентов** диалогового окна **Свойства публикации** позволяет получить доступ к параметрам учетных записей, от имени которых запускаются и соединяются с компьютерами в топологии репликации следующие агенты.  
  
-   Агент моментальных снимков для всех публикаций.  
  
-   Агент чтения журнала для всех публикаций транзакций. У каждой базы данных, опубликованной для репликации транзакций, может быть только один агент чтения журнала. Изменение настроек агента чтения журнала затрагивает все публикации транзакций в базе данных.  
  
-   Агент чтения очереди для публикаций транзакций, допускающих подписки, обновляемые посредством очередей. Для каждой базы распространителя существует только один агент чтения очереди. Изменение агента чтения очереди затрагивает все публикации транзакций с обновляемыми посредством очередей подписками, использующими одну и ту же базу данных распространителя. Дополнительные сведения о настройках безопасности для агента чтения очереди см. в статье [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Дополнительные сведения о настройках безопасности и разрешениях, необходимых для каждого агента, см. в разделе [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="options"></a>Параметры  
 **Настройки безопасности** или **Создать агент**  
 Если задание агента уже было создано, щелкните **Настройки безопасности** , чтобы открыть диалоговое окно для изменения настроек безопасности агента. Если задание агента не было создано, щелкните **Создать агент** , чтобы создать его и задать настройки безопасности.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Безопасность и защита (репликация)](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
