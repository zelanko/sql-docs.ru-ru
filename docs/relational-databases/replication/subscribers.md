---
description: Подписчики
title: Подписчики | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016
ms.openlocfilehash: be8ccf0bbaf2efa80c9b0e48e39a0743d63b0c75
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97479615"
---
# <a name="subscribers"></a>Подписчики
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Укажите подписчики [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или отличные от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчики, которые будут получать подписку на выбранную публикацию.


[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Параметры  
 **Подписчики**  
 Установите флажок на сетке, чтобы выбрать соответствующий источник данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источник данных в качестве подписчика публикации, выбранной на странице **Публикация**. Если подписчика нет в списке, выберите пункт **Добавить подписчик** или **Добавить подписчик SQL Server**.  
  
 **База данных подписки**  
 Данные и операции в данном столбце зависят от типов подписчиков, перечисленных в столбце **Подписчики** .  
  
-   Для подписчиков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите из списка **База данных подписки** базу данных или создайте новую базу данных с помощью команды **Создать базу данных** в этом же списке.  
  
    > [!NOTE]  
    >  Если издатель выбран также в качестве подписчика, база данных подписки должна отличаться от базы данных публикации.  
  
-   Для подписчиков, отличных от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , база данных подписки не отображается. В поле **Имя источника данных** диалогового окна **Добавление сервера, отличного от подписчика SQL Server** укажите базу данных вместе с другими сведениями о соединении. Чтобы открыть это диалоговое окно, нажмите кнопку **Добавить подписчик** , а затем выберите пункт **Добавить подписчик, отличный от подписчика SQL Server**.  
  
 **Добавить подписчик**  
 Добавьте сервер в список серверов, которые могут быть включены в качестве подписчиков. Данная кнопка отображается, когда выполняются все перечисленные далее условия.  
  
-   Выбранная публикация является публикацией транзакций или моментальных снимков без поддержки обновляемых подписок.  
  
    > [!NOTE]  
    >  Если публикация, на которую выполняется подписка, имеет подписки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но еще не подготовлена для подписчиков, не являющихся[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , добавить подписку, не являющуюся[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , невозможно.  
  
-   Подписка является принудительной.  
  
-   Издателем выбранной публикации является [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздней версии.  
  
 При нажатии кнопки **Добавить подписчик** отображается меню с двумя пунктами: **Добавить подписчик SQL Server** и **Добавить подписчик, отличный от подписчика SQL Server**. Чтобы добавить подписчик Oracle или IBM DB2, выберите пункт **Добавить подписчик, отличный от подписчика SQL Server** .  
  
 **Добавить подписчик SQL Server**  
 Добавьте сервер в список серверов, которые могут быть включены в качестве подписчиков. Данная кнопка отображается при выполнении одного или нескольких из перечисленных ниже условий.  
  
-   Выбранная публикация является публикацией слиянием, публикацией моментальными снимками или публикацией транзакций с поддержкой обновляемых подписок.  
  
-   Подписка является подпиской по запросу.  
  
-   Версия издателя выбранной публикации ниже [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Для более ранних версий данная кнопка отображается при выполнении одного или нескольких из перечисленных ниже условий.  
  
    -   Вы являетесь членом предопределенной роли сервера **sysadmin** на издателе.  
  
    -   Подписка добавлена на странице **Подписчики** в диалоговом окне **Свойства издателя** .  
  
    -   Публикация допускает анонимные подписки.  
  
## <a name="see-also"></a>См. также:  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
