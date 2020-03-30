---
title: Объекты обмена сообщениями компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], host databases
- Database Mail [SQL Server], messaging objects
- mail host databases [SQL Server]
- host databases [Database Mail]
ms.assetid: 5aa2886e-1db1-4066-85df-57ccf4538c54
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8eb132920a6b51303e5725ecdb770dd742972f42
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "70809946"
---
# <a name="database-mail-messaging-objects"></a>Объекты обмена сообщениями компонента Database Mail
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Для размещения компонента Database Mail используется база данных обслуживания почты **msdb** . Она содержит хранимые процедуры и объекты обмена сообщениями компонента Database Mail. Используя входящий в среду Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] мастер настройки компонента Database Mail, можно активировать компонент Database Mail, создавать и администрировать профили и учетные записи и настраивать параметры компонента Database Mail.  
  
##  <a name="objects-in-msdb-database"></a><a name="ComponentsAndConcepts"></a> Объекты в базе данных **msdb**  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] msdb **msdb** . Однако компонент Database Mail не пользуется сетевыми возможностями компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Поэтому для использования компонента Database Mail пользователи не должны создавать конечную точку компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Для взаимодействия с [!INCLUDE[vstecado](../../includes/vstecado-md.md)] внешний процесс компонента Database Mail использует стандартное соединение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если компонент Database Mail включен, в базе данных **msdb** доступны следующие объекты:  
  
 Эти объекты являются интерфейсом для компонента Database Mail в рамках базы данных обслуживания почты. Остальные установленные объекты предназначены для реализации выполнения функций, предоставляемых перечисленными выше объектами. Тем не менее они зарезервированы для внутреннего использования.  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|[sysmail_allitems (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)|**View** (Вид)|Содержит список сообщений, полученных компонентом Database Mail.|  
|[sysmail_event_log (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)|**View** (Вид)|Содержит список сообщений, касающихся работы [Database Mail External Program](../../relational-databases/database-mail/database-mail-external-program.md).|  
|[sysmail_faileditems (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)|**View** (Вид)|Содержит сведения о сообщениях, которые компоненту Database Mail не удалось отправить.|  
|[sysmail_mailattachments (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md)|**View** (Вид)|Содержит сведения о вложениях в сообщениях компонента Database Mail.|  
|[sysmail_sentitems (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md)|**View** (Вид)|Содержит сведения о сообщениях, отправленных с помощью компонента Database Mail.|  
|[sysmail_unsentitems (Transact-SQL)](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md)|**View** (Вид)|Содержит сведения о сообщениях, которые компонент Database Mail в настоящий момент пытается отправить.|  
|[sp_send_dbmail (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)|**Хранимая процедура**|Отправляет сообщения электронной почты при помощи компонента Database Mail.|  
|[sysmail_delete_log_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md)|**Хранимая процедура**|Удаляет сообщения из журнала компонента Database Mail.|  
|[sysmail_delete_mailitems_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)|**Хранимая процедура**|Удаляет почтовые элементы из очереди компонента Database Mail.|  
|[sysmail_help_status_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql.md)|**Хранимая процедура**|Показывает, запущен ли компонент Database Mail.|  
|[sysmail_start_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)|**Хранимая процедура**|Запускает объекты компонента Service Broker, используемые внешней программой. Эти объекты запускаются по умолчанию.|  
|[sysmail_stop_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)|**Хранимая процедура**|Останавливает объекты компонента Service Broker, используемые внешней программой.|  
  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
