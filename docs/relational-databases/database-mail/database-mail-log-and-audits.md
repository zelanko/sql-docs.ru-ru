---
title: "Ведение журнала и аудит компонента Database Mail | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "аудит [SQL Server]"
  - "компонент Database Mail [SQL Server], аудит"
  - "журналы [компонент Database Mail]"
  - "аудиты [SQL Server], компонент Database Mail"
  - "компонент Database Mail [SQL Server], ведение журналов"
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
caps.latest.revision: 30
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 30
---
# Ведение журнала и аудит компонента Database Mail
  Регистрация в Database Mail спроектирована таким образом, чтобы обеспечить способ локализации и исправления неполадок. Компонент Database Mail хранит сведения о регистрации в базе данных **msdb** . Сведения о содержимом сообщений электронной почты Database Mail, их состояниях, а также о любых полученных сообщениях, например сообщениях об ошибках, регистрируются в Database Mail и могут использоваться для аудита или обеспечения безопасности.  
  
## Журналы компонента Database Mail  
 Таблицы в базе данных **msdb** записывают журнал из [Database Mail External Program](../../relational-databases/database-mail/database-mail-external-program.md). [Представления компонента Database Mail (Transact-SQL)](../../relational-databases/system-catalog-views/database-mail-views-transact-sql.md) позволяют устранять неполадки в таблицах. В представлении [sysmail_event_log (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md) отображаются ошибки, если компонент Service Broker не может запустить внешнюю программу, если в этой внешней программе возникли ошибки при работе с сетью или сервер SMTP отказался принять сообщение электронной почты. В случае события, которое внешняя программа не может записать в таблицы **msdb** , она записывает ошибки в журнал событий приложений Windows.  
  
 Внутренние таблицы в базе данных **msdb** содержат электронные сообщения и вложения, присланные компонентом Database Mail, а также текущее состояние каждого сообщения. Компонент Database Mail обновляет эти таблицы при каждом обработанном сообщении.  
  
## Задачи аудита компонента Database Mail  
  
|||  
|-|-|  
|**Обзор журналов компонента Database Mail и управление ими**|**Ссылка на раздел**|  
|Проверьте состояние доставки отдельного сообщения|[Проверка состояния сообщений электронной почты, отправленных при помощи компонента Database Mail](../../relational-databases/database-mail/check-the-status-of-e-mail-messages-sent-with-database-mail.md)|  
|Очистите сообщения, вложения и записи журнала компонента Database Mail|[sysmail_delete_mailitems_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)<br /><br /> [sysmail_delete_log_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md)|  
|Заархивируйте сообщения и журналы компонента Database Mail|[Создание задания агента SQL Server по архивации сообщений компонента Database Mail и журналов событий базы данных](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)|  
  
## См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  