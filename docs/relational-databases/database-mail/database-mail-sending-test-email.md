---
title: Отправка тестового электронного сообщения с компонентом Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 04/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95e4e365ed1ec89050ceb8c3765e6a217f819cd3
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67585268"
---
# <a name="send-a-test-email-with-database-mail"></a>Отправка тестового электронного сообщения с компонентом Database Mail  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В диалоговом окне "Отправка тестового сообщения" можно проверить отправку сообщений с использованием заданного профиля.

## <a name="permissions"></a>Разрешения

Для работы в диалоговом окне "Отправка тестового электронного сообщения" необходимо членство в предопределенной роли сервера sysadmin. Пользователи, не являющиеся членами предопределенной роли сервера sysadmin, могут проверить отправку сообщений компонентом Database Mail с помощью хранимой процедуры [sp_send_dbmail](../system-stored-procedures/sp-send-dbmail-transact-sql.md).

## <a name="procedure"></a>Процедура

1. В обозревателе объектов [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) подключите экземпляр ядра SQL Server, в котором настроен компонент Database Mail, разверните"Управление", щелкните правой кнопкой мыши Database Mail, а затем выберите "Отправить тестовое сообщение". Если профилей в компоненте Database Mail нет, откроется диалоговое окно создания профиля пользователя с помощью мастера настройки компонента Database Mail.
1. В диалоговом окне **Отправка тестового сообщения** от <instance name> в поле "Профиль компонента Database Mail" выберите профиль, который нужно проверить.
1. В поле **Кому** введите адрес электронной почты получателя тестового сообщения.
1. В поле **Тема** введите строку с темой тестового сообщения. Измените тему сообщения по умолчанию, чтобы упростить диагностику.
1. В поле **Текст сообщения** введите текст тестового сообщения. Измените тему сообщения по умолчанию, чтобы упростить диагностику.
1. Нажмите кнопку **Отправить тестовое сообщение**, чтобы отправить электронное сообщение в очередь компонента Database Mail.
1. При отправке тестового электронного сообщения откроется диалоговое окно "Тестовое сообщение компонента Database Mail". Запомните или запишите число в поле "Сообщение отправлено". Это идентификатор mailitem_id тестового электронного сообщения. Нажмите кнопку "ОК".
1. На панели инструментов нажмите кнопку "Создать запрос", чтобы открыть окно редактора запросов. Выполните следующую инструкцию T-SQL, чтобы определить состояние тестового сообщения:

    ```sql
    SELECT * FROM msdb.dbo.sysmail_allitems 
    WHERE mailitem_id = <the mailitem_id from the previous step> ;
    ```

    Значение столбца sent_status указывает, было ли отправлено тестовое электронное сообщение.

1. Если произошла ошибка, выполните следующую инструкцию, чтобы просмотреть соответствующее сообщение:

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    ```sql
    SELECT * FROM msdb.dbo.sysmail_event_log 
    WHERE mailitem_id = <the mailitem_id from the previous step> ;
    ```


##  <a name="RelatedContent"></a> См. также 
  
-   [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)
-   [Объекты обмена сообщениями компонента Database Mail](../../relational-databases/database-mail/database-mail-messaging-objects.md)
-   [Внешняя программа компонента Database Mail](../../relational-databases/database-mail/database-mail-external-program.md)
-   [Ведение журнала и аудит компонента Database Mail](../../relational-databases/database-mail/database-mail-log-and-audits.md)
-   [Настройка почты агента SQL Server на использование компонента Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)
  
  
