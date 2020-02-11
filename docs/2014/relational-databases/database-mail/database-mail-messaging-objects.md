---
title: Объекты обмена сообщениями компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 3657e45d18ac84ad737a016150692730f736b55f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62917719"
---
# <a name="database-mail-messaging-objects"></a>Объекты обмена сообщениями компонента Database Mail
  Для размещения компонента Database Mail используется база данных обслуживания почты **msdb** . Она содержит хранимые процедуры и объекты обмена сообщениями компонента Database Mail. Используя входящий в среду Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] мастер настройки компонента Database Mail, можно активировать компонент Database Mail, создавать и администрировать профили и учетные записи и настраивать параметры компонента Database Mail.  
  
##  <a name="ComponentsAndConcepts"></a> Объекты в базе данных **msdb**  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] msdb **msdb** . Однако компонент Database Mail не пользуется сетевыми возможностями компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Поэтому для использования компонента Database Mail пользователи не должны создавать конечную точку компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Для взаимодействия с [!INCLUDE[vstecado](../../includes/vstecado-md.md)] внешний процесс компонента Database Mail использует стандартное соединение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если компонент Database Mail включен, в базе данных **msdb** доступны следующие объекты:  
  
 Эти объекты являются интерфейсом для компонента Database Mail в рамках базы данных обслуживания почты. Остальные установленные объекты предназначены для реализации выполнения функций, предоставляемых перечисленными выше объектами. Тем не менее они зарезервированы для внутреннего использования.  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|[sysmail_allitems (Transact-SQL)](/sql/relational-databases/system-catalog-views/sysmail-allitems-transact-sql)|`View`|Содержит список сообщений, полученных компонентом Database Mail.|  
|[sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql)|`View`|Содержит список сообщений, касающихся работы [Database Mail External Program](database-mail-external-program.md).|  
|[sysmail_faileditems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-faileditems-transact-sql)|`View`|Содержит сведения о сообщениях, которые компоненту Database Mail не удалось отправить.|  
|[sysmail_mailattachments &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql)|`View`|Содержит сведения о вложениях в сообщениях компонента Database Mail.|  
|[sysmail_sentitems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-sentitems-transact-sql)|`View`|Содержит сведения о сообщениях, отправленных с помощью компонента Database Mail.|  
|[sysmail_unsentitems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql)|`View`|Содержит сведения о сообщениях, которые компонент Database Mail в настоящий момент пытается отправить.|  
|[sp_send_dbmail &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql)|`Stored Procedure`|Отправляет сообщения электронной почты при помощи компонента Database Mail.|  
|[sysmail_delete_log_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|`Stored Procedure`|Удаляет сообщения из журнала компонента Database Mail.|  
|[sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)|`Stored Procedure`|Удаляет почтовые элементы из очереди компонента Database Mail.|  
|[sysmail_help_status_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql)|`Stored Procedure`|Показывает, запущен ли компонент Database Mail.|  
|[sysmail_start_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql)|`Stored Procedure`|Запускает объекты компонента Service Broker, используемые внешней программой. Эти объекты запускаются по умолчанию.|  
|[sysmail_stop_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql)|`Stored Procedure`|Останавливает объекты компонента Service Broker, используемые внешней программой.|  
  

  
## <a name="see-also"></a>См. также:  
 [Database Mail](database-mail.md)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
