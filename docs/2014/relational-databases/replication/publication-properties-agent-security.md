---
title: Свойства публикации, страница "Безопасность агентов" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.agentsecurity.f1
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5b8f38f877a6a46be70fcfafd2ca3c79fca415b6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52749026"
---
# <a name="publication-properties-agent-security"></a>Свойства публикации, агент безопасности
  Страница **Безопасность агентов** диалогового окна **Свойства публикации** позволяет получить доступ к параметрам учетных записей, от имени которых запускаются и соединяются с компьютерами в топологии репликации следующие агенты.  
  
-   Агент моментальных снимков для всех публикаций.  
  
-   Агент чтения журнала для всех публикаций транзакций. У каждой базы данных, опубликованной для репликации транзакций, может быть только один агент чтения журнала. Изменение настроек агента чтения журнала затрагивает все публикации транзакций в базе данных.  
  
-   Агент чтения очереди для публикаций транзакций, допускающих подписки, обновляемые посредством очередей. Для каждой базы распространителя существует только один агент чтения очереди. Изменение агента чтения очереди затрагивает все публикации транзакций с обновляемыми посредством очередей подписками, использующими одну и ту же базу данных распространителя. Дополнительные сведения о настройках безопасности для агента чтения очереди см. в статье [Просмотр и изменение параметров безопасности репликации](security/view-and-modify-replication-security-settings.md).  
  
 Дополнительные сведения о настройках безопасности и разрешениях, необходимых для каждого агента, см. в разделе [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
## <a name="options"></a>Параметры  
 **Настройки безопасности** или **Создать агент**  
 Если задание агента уже было создано, щелкните **Настройки безопасности** , чтобы открыть диалоговое окно для изменения настроек безопасности агента. Если задание агента не было создано, щелкните **Создать агент** , чтобы создать его и задать настройки безопасности.  
  
## <a name="see-also"></a>См. также  
 [Create a Publication](publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](publish/view-and-modify-publication-properties.md)   
 [Публикация данных и объектов базы данных](publish/publish-data-and-database-objects.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Безопасность и защита (репликация)](security/security-and-protection-replication.md)  
  
  
