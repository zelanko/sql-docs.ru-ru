---
title: "Занятие 1. Создание учетных записей Windows для репликации | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
caps.latest.revision: "17"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 422f5bc66dc5b31889d4f790d61b5b95abf2fa7e
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>Занятие 1. Создание учетных записей Windows для репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] На этом занятии будут созданы учетные записи Windows для запуска агентов репликации. На локальном сервере будут созданы отдельные учетные записи Windows для следующих агентов:  
  
|Агент|Местоположение|Имя учетной записи|  
|---------|------------|----------------|  
|агент моментальных снимков|Издатель|\<*имя_компьютера*>\repl_snapshot|  
|Агент чтения журнала.|Издатель|\<*имя_компьютера*>\repl_logreader|  
|Агент распространителя|Издатель и подписчик|\<*имя_компьютера*>\repl_distribution|  
|Агент слияния.|Издатель и подписчик|\<*имя_компьютера*>\repl_merge|  
  
> [!NOTE]  
> В учебниках по репликации издатель и распространитель совместно используют один и тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Издатель и подписчик могут совместно использовать один и тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но это не является обязательным. Если издатель и подписчик совместно используют один и тот же экземпляр, то не требуется выполнять шаги по созданию учетных записей на подписчике.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>Создание локальных учетных записей Windows для агентов репликации на издателе  
  
1.  Откройте в издателе оснастку **Управление компьютером** из папки **Администрирование** панели управления.  
  
2.  В оснастке **Служебные программы**разверните узел **Локальные пользователи и группы**.  
  
3.  Щелкните правой кнопкой мыши значок **Пользователи** , а затем выберите пункт **Новый пользователь…**  
  
4.  Введите **repl_snapshot** в поле **Имя пользователя** , укажите пароль и другие необходимые сведения, а затем нажмите кнопку **Создать** , чтобы создать учетную запись repl_snapshot.  
  
5.  Повторите предыдущий шаг, чтобы создать учетные записи repl_logreader, repl_distribution и repl_merge.  
  
6.  Щелкните **Закрыть**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>Создание локальных учетных записей Windows для агентов репликации на подписчике  
  
1.  Откройте в подписчике оснастку **Управление компьютером** из папки **Администрирование** панели управления.  
  
2.  В оснастке **Служебные программы**разверните узел **Локальные пользователи и группы**.  
  
3.  Щелкните правой кнопкой мыши значок **Пользователи** , а затем выберите пункт **Новый пользователь…**  
  
4.  Введите **repl_distribution** в поле **Имя пользователя** , укажите пароль и другие необходимые сведения, затем нажмите **Создать** , чтобы создать учетную запись repl_distribution.  
  
5.  Повторите предыдущий шаг, чтобы создать учетную запись repl_merge.  
  
6.  Щелкните **Закрыть**.  
  
## <a name="next-steps"></a>Next Steps  
Создание учетных записей Windows для агентов репликации успешно выполнено. Далее предстоит настроить папку моментальных снимков. См. раздел [Занятие 2. Подготовка папки моментальных снимков](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md).  
  
## <a name="see-also"></a>См. также:  
[Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
  
