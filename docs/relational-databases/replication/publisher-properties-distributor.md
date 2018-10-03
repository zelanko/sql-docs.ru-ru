---
title: Свойства издателя — распространитель | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b010746d438ae320452839ec5b959dec16da732c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731742"
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
  
  
