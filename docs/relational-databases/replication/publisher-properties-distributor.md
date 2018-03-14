---
title: "Свойства издателя — распространитель | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fdbb73e5adcb6da6ba31ab69cfdc99840507fd80
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="publisher-properties---distributor"></a>Свойства издателя — распространитель
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Свойства издателя** позволяет просматривать и изменять свойства, относящиеся к связи между издателем и его распространителем.  
  
## <a name="options"></a>Параметры  
 **Соединение агента с издателем**  
 Укажите контекст, в котором следующие агенты выполняют соединения распространителя с издателем.  
  
-   Агент чтения очереди для публикаций транзакций, допускающих подписки, обновляемые посредством очередей.  
  
-   Агент моментальных снимков и агент чтения журнала для публикаций Oracle.  
  
 Выберите **Выполнять олицетворение учетной записи процесса агента** для соединения с издателем при помощи контекста учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которой работают эти агенты, или выберите **Проверка подлинности SQL Server**и введите **Имя входа** и **Пароль**. Рекомендуется выбрать **Выполнять олицетворение учетной записи процесса агента**. Дополнительные сведения о безопасности агента см. в статье [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Учетные записи Windows, с которыми работают эти агенты, задаются в мастере создания публикаций. Эти учетные записи могут быть изменены двумя способами.  
  
-   В диалоговом окне **Свойства распространителя** для агента чтения очереди.  
  
-   В диалоговом окне **Свойства публикации** для агента моментальных снимков и агента чтения журнала.  
  
 **Разное**  
 Свойства **Тип издателя** и **Имя базы данных распространителя** доступны только для чтения. Свойство **Папка моментальных снимков по умолчанию** может быть изменено. Дополнительные сведения о папке моментальных снимков см. в статье [Организация безопасности папки моментальных снимков](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Справочник по свойствам (репликация)](../../relational-databases/replication/properties-reference-replication.md)  
  
  
