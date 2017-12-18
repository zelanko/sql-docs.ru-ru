---
title: "Урок 1. Публикация данных с помощью репликации транзакций | Документация Майкрософт"
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
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b6d053d9a0e80785e375fdb1f796ddf01894d993
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-1-publishing-data-using-transactional-replication"></a>Урок 1. Публикация данных с помощью репликации транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] На этом занятии с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] создается публикация транзакций с целью публикации фильтрованного подмножества таблицы **Product** из образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Также в список доступа к публикации (PAL) добавляется имя входа SQL Server, используемое агентом распространителя. Перед началом работы с этим учебником необходимо завершить работу с предыдущим учебником, [Подготовка сервера к репликации](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
### <a name="to-create-a-publication-and-define-articles"></a>Создание публикации и определение статей  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Разверните папку **Репликация** , щелкните правой кнопкой мыши папку **Локальные публикации** и выберите пункт **Создать публикацию**.  
  
    Будет запущен мастер настройки публикации.  
  
3.  На странице «База данных публикации» выберите [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]и нажмите кнопку **Далее**.  
  
4.  На странице «Тип публикации» выберите **Публикация транзакций**и нажмите кнопку **Далее**.  
  
5.  На странице "Статьи" разверните узел **Таблицы** , установите флажок **Product** , затем разверните **Product** и снимите флажки **ListPrice** и **StandardCost** . Нажмите кнопку **Далее**.  
  
6.  На странице «Фильтр строк таблицы» нажмите кнопку **Добавить**.  
  
7.  В диалоговом окне **Добавление фильтра** щелкните столбец **SafetyStockLevel** , щелкните стрелку вправо, чтобы добавить столбец в предложение WHERE инструкции фильтра запроса, и измените предложение WHERE следующим образом.  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  Нажмите кнопку **ОК**, а затем нажмите кнопку **Далее**.  
  
9. Установите флажок **Создать моментальный снимок немедленно и обеспечить доступ к нему для инициализации подписок** и нажмите кнопку **Далее**.  
  
10. На странице "Безопасность агента" снимите флажок **Использовать настройки безопасности агента моментальных снимков** .  
  
11. Для агента моментальных снимков щелкните **Настройки безопасности**, введите \<*Имя_компьютера>***\repl_snapshot** в поле **Учетная запись процесса**, укажите пароль для этой учетной записи и нажмите кнопку **ОК**.  
  
12. Повторите предыдущий шаг, чтобы установить repl_logreader в качестве учетной записи процесса для агента чтения журнала, а затем нажмите кнопку **Готово**.  
  
13. На странице "Завершение работы мастера" введите **AdvWorksProductTrans** в поле **Имя публикации** и нажмите кнопку **Готово**.  
  
14. После создания публикации нажмите кнопку **Закрыть** , чтобы закрыть мастер.  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Просмотр состояния создания моментального снимка  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** щелкните правой кнопкой мыши публикацию **AdvWorksProductTrans**и выберите пункт **Просмотр состояния агента моментальных снимков**.  
  
3.  Отобразится текущее состояние задания агента моментальных снимков для публикации. Перед тем как перейти к следующему занятию, убедитесь, что задание моментального снимка выполнено успешно.  
  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a>Добавление имени входа агента распространителя в список доступа к публикации  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  В папке **Локальные публикации** щелкните правой кнопкой мыши публикацию **AdvWorksProductTrans**и выберите пункт **Свойства**.  
  
    Откроется диалоговое окно **Свойства публикации** .  
  
3.  Выберите страницу **Список доступа к публикации** и нажмите кнопку **Добавить**.  
  
4.  В диалоговом окне **Добавление доступа к публикации** выберите *<Имя_компьютера>***\repl_distribution** и нажмите кнопку **ОК**. Нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Следующие шаги  
Публикация транзакций успешно создана. Далее будет создана подписка на эту публикацию. См. [Занятие 2. Создание подписки на публикацию транзакций](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
## <a name="see-also"></a>См. также:  
[Фильтрация опубликованных данных](../../relational-databases/replication/publish/filter-published-data.md)  
[Определение статьи](../../relational-databases/replication/publish/define-an-article.md)  
[Создание и применение моментального снимка](../../relational-databases/replication/create-and-apply-the-snapshot.md)  
  
  
  
