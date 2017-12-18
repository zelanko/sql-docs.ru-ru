---
title: "Занятие 2. Создание подписки на публикацию транзакций | Документация Майкрософт"
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
applies_to: SQL Server 2016
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b361f84ecf464ee66936c88ff9f6114d4203bf23
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a>Занятие 2. Создание подписки на публикацию транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] На этом занятии с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] будет создана подписка. Приступать к этому занятию нужно только по завершении предыдущего: [Занятие 1. Публикация данных с помощью репликации транзакций](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md).  
  
### <a name="to-create-the-subscription"></a>Создание подписки  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** щелкните правой кнопкой мыши публикацию **AdvWorksProductTrans** и выберите команду **Создать подписку**.  
  
    Откроется мастер создания подписки.  
  
3.  На странице «Публикация» выберите публикацию **AdvWorksProductTrans**и нажмите кнопку **Далее**.  
  
4.  На странице «Расположение агента распространителя» установите флажок **Выполнять все агенты на распространителе**и нажмите кнопку **Далее**.  
  
5.  Если имя экземпляра подписчика не отображается, на странице «Подписчики» нажмите кнопку **Добавить подписчик**, выберите **Добавить подписчик SQL Server**, в диалоговом окне **Соединение с сервером** введите имя экземпляра подписчика, затем нажмите кнопку **Соединить**.  
  
6.  На странице "Подписчики" выберите имя экземпляра сервера подписчика, а затем выберите **<New Database>** в поле **База данных подписки**.  
  
7.  В диалоговом окне **Создание базы данных** в поле **Имя базы данных** введите **ProductReplica** , нажмите кнопку **ОК**, затем **Далее**.  
  
8.  В диалоговом окне **Безопасность агента распространителя** нажмите кнопку с многоточием (**…**), введите \<*имя_компьютера>***\repl_distribution** в поле **Учетная запись процесса**, а затем введите пароль для этой учетной записи, нажмите кнопки **ОК** и **Далее**.  
  
9. Нажмите кнопку **Готово** , чтобы принять значения по умолчанию на оставшихся страницах и завершить работу мастера.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Установка разрешений базы данных на подписчике  
  
1.  Подключитесь к подписчику в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], последовательно разверните узлы **Базы данных**, **ProductReplica**и **Безопасность**, щелкните правой кнопкой мыши элемент **Пользователи**и выберите пункт **Создать пользователя**.  
  
2.  На странице **Общие** в списке **Тип пользователя** выберите **Пользователь Windows**.  
  
3.  Выберите поле **Имя пользователя**, нажмите кнопку с многоточием (…), в поле **Введите имя объекта** введите <имя_компьютера>**\repl_distribution**, щелкните **Проверить имена**, а затем нажмите кнопку **ОК**.  
  
4.  Чтобы создать пользователя, на странице **Членство** в поле **Членство в роли базы данных** выберите **db_owner** и нажмите кнопку **ОК**.  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>Просмотр состояния синхронизации подписки  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** разверните публикацию **AdvWorksProductTrans** , щелкните правой кнопкой мыши подписку в базе данных **ProductReplica** и выберите пункт **Просмотр состояния синхронизации**.  
  
    Отобразится текущее состояние синхронизации подписки.  
  
3.  Если подписка не отображается под публикацией **AdvWorksProductTrans**, нажмите клавишу F5 для обновления списка.  
  
## <a name="next-steps"></a>Следующие шаги  
Создание подписки на публикацию транзакций успешно завершено. Ввиду того, что агент распространителя для этой подписки постоянно запущен, подписка инициализируется при создании. Далее необходимо использовать трассировочные токены, чтобы проверить выполнение репликации изменений и определить задержку. См. раздел [Lesson 3: Validating the Subscription and Measuring Latency](../../relational-databases/replication/lesson-3-validating-the-subscription-and-measuring-latency.md).  
  
## <a name="see-also"></a>См. также:  
[Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Создание принудительной подписки](../../relational-databases/replication/create-a-push-subscription.md)  
[Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
