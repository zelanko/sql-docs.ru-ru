---
title: "Свойства подписчика | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b84b8e31083934703db11e060520ec77f9dd5417
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="subscriber-properties"></a>Свойства подписчика
  Диалоговое окно **Свойства подписчика** содержит сведения, относящиеся к подписчикам, использующим версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предшествующие [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="options"></a>Параметры  
 **Соединение агента с подписчиком**  
 Контекст, в котором агент распространителя и агент слияния устанавливают соединение от распространителя к подписчику. Применяется только к версиям, предшествующим [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Выберите **Выполнять олицетворение учетной записи процесса агента** для соединения с подписчиком при помощи контекста учетной записи агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на распространителе или укажите **Проверка подлинности SQL Server**, а затем введите значения в поля **Имя входа** и **Пароль**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выбрать пункт **Выполнять олицетворение учетной записи процесса агента**.  
  
 Для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий данные о соединении указываются для каждой подписки в мастере создания подписки, их можно изменить в диалоговом окне **Свойства подписки** .  
  
 **Расписания агентов по умолчанию**  
 Расписание по умолчанию, используемое в мастере создания подписки для подписчиков, использующих версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предшествующие [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 **Разное**  
 Содержит сведения о подписчике и типе подписчика.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Справочник по свойствам (репликация)](../../relational-databases/replication/properties-reference-replication.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
