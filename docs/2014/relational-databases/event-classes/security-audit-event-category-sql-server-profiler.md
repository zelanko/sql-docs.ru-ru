---
title: Категория событий Security Audit (приложение SQL Server Profiler) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [SQL Server], Security Audit event category
- SQL Server event classes, Security Audit event category
ms.assetid: e64f7695-2f23-4adb-b83d-52f147cc1a2f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9f2f854c7a6dbd0d1ab569f87bf053a5b9f45058
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044226"
---
# <a name="security-audit-event-category-sql-server-profiler"></a>Категория событий Security Audit (приложение SQL Server Profiler)
  Категория событий **Security Audit** включает в себя события аудита безопасности.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Audit Add DB User, класс событий](audit-add-db-user-event-class.md)|Указывает, что имя входа пользователя базы данных было добавлено или удалено из базы данных.|  
|[Audit Add Login to Server Role, класс событий](audit-add-login-to-server-role-event-class.md)|Указывает, что имя входа было добавлено или удалено из предопределенной роли сервера.|  
|[Audit Add Member to DB Role, класс событий](audit-add-member-to-db-role-event-class.md)|Указывает, что имя входа было добавлено или удалено из роли.|  
|[Audit Add Role, класс событий](audit-add-role-event-class.md)|Указывает, что роль базы данных была добавлена или удалена из базы данных.|  
|[Audit Addlogin, класс событий](audit-addlogin-event-class.md)|Указывает, что имя входа было добавлено или удалено.|  
|[Audit App Role Change Password, класс событий](audit-app-role-change-password-event-class.md)|Указывает, что пароль для роли приложения был изменен.|  
|[Класс событий Audit Backup и Restore](audit-backup-and-restore-event-class.md)|Указывает, что была выполнена инструкция по восстановлению или резервному копированию.|  
|[Audit Broker Conversation, класс событий](broker-conversation-event-class.md)|Уведомляет о сообщениях аудита, относящихся к безопасности диалога компонента Service Broker.|  
|[Audit Broker Login, класс событий](audit-broker-login-event-class.md)|Уведомляет о сообщениях аудита, относящихся к транспортной безопасности компонента Service Broker.|  
|[Audit Change Audit, класс событий](audit-change-audit-event-class.md)|Указывает, что были внесены изменения в трассировку аудита.|  
|[Класс событий Audit Change Database Owner](audit-change-database-owner-event-class.md)|Указывает, что разрешения на изменение владельца базы данных были проверены.|  
|[Audit Database Management, класс событий](audit-database-management-event-class.md)|Указывает, что база данных была создана, изменена или удалена.|  
|[Audit Database Mirroring Login, класс событий](audit-database-mirroring-login-event-class.md)|Уведомляет о сообщениях аудита, относящихся к транспортной безопасности зеркального отображения базы данных.|  
|[Audit Database Object Access, класс событий](audit-database-object-access-event-class.md)|Указывает, что был получен доступ к объекту базы данных, например схеме.|  
|[Audit Database Object GDR, класс событий](audit-database-object-gdr-event-class.md)|Указывает, что произошло событие GDR для объекта базы данных.|  
|[Класс событий Audit Database Object Management](audit-database-object-management-event-class.md)|Указывает, что инструкция CREATE, ALTER или DROP была выполнена в отношении объекта базы данных.|  
|[Класс событий Audit Database Object Take Ownership](audit-database-object-take-ownership-event-class.md)|Указывает, что в области базы данных произошло изменение владельца объектов.|  
|[Audit Database Operation, класс событий](audit-database-operation-event-class.md)|Указывает, что выполнена одна из операций, таких как уведомление запроса контрольной точки или подписки.|  
|[Audit Database Principal Impersonation, класс событий](audit-database-principal-impersonation-event-class.md)|Указывает на то, что в области базы данных произошло олицетворение.|  
|[Audit Database Principal Management, класс событий](audit-database-principal-management-event-class.md)|Указывает, что участники были созданы, изменены или удалены из базы данных.|  
|[Audit Database Scope GDR, класс событий](audit-database-scope-gdr-event-class.md)|Указывает, что пользователь в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]имеет разрешение GRANT, REVOKE или Deny для разрешения инструкции.|  
|[Audit DBCC, класс событий](audit-dbcc-event-class.md)|Указывает, что была выполнена команда DBCC.|  
|[Класс событий Audit Fulltext](audit-fulltext-event-class.md)|Указывает, что произошло полнотекстовое событие.|  
|[Audit Login Change Password, класс событий](audit-login-change-password-event-class.md)|Указывает, что пользователь изменил пароль, используемый для входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Audit Login Change Property, класс событий](audit-login-change-property-event-class.md)|Указывает, что для изменения свойства имени входа была использована хранимая процедура **sp_defaultdb**, **sp_defaultlanguage**или инструкция ALTER LOGIN.|  
|[Audit Login, класс событий](audit-login-event-class.md)|Указывает, что пользователь успешно выполнил вход на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Audit Login Failed, класс событий](audit-login-failed-event-class.md)|Указывает, что пользователь выполнил попытку входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая завершилась неудачно.|  
|[Audit Login GDR, класс событий](audit-login-gdr-event-class.md)|Указывает, что право входа в систему [!INCLUDE[msCoName](../../includes/msconame-md.md)] было добавлено или удалено.|  
|[Audit Logout, класс событий](audit-logout-event-class.md)|Указывает, что пользователь вышел из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Класс событий Audit Object Derived Permission](audit-object-derived-permission-event-class.md)|Указывает, что инструкция CREATE, ALTER или DROP была выполнена в отношении объекта.|  
|[Audit Schema Object Access, класс событий](audit-schema-object-access-event-class.md)|Указывает, что было использовано разрешение объекта (такое как SELECT).|  
|[Audit Schema Object GDR, класс событий](audit-schema-object-gdr-event-class.md)|Указывает на выполнение пользователем инструкции GRANT, REVOKE или DENY по поводу разрешения для объекта схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Audit Schema Object Management, класс событий](audit-schema-object-management-event-class.md)|Указывает, что объект сервера был создан, изменен или удален.|  
|[Audit Schema Object Take Ownership, класс событий](audit-schema-object-take-ownership-event-class.md)|Указывает, что была выполнена проверка разрешений на изменение владельца объекта схемы.|  
|[Audit Server Alter Trace, класс событий](audit-server-alter-trace-event-class.md)|Указывает, что была выполнена проверка разрешения ALTER TRACE.|  
|[Audit Server Object GDR, класс событий](audit-server-object-gdr-event-class.md)|Указывает, что произошло событие GDR для объекта схемы.|  
|[Audit Server Object Management, класс событий](audit-server-object-management-event-class.md)|Указывает, что событие CREATE, ALTER или DROP произошло в отношении объекта сервера.|  
|[Audit Server Object Take Ownership, класс событий](audit-server-object-take-ownership-event-class.md)|Указывает, что изменен владелец объекта сервера.|  
|[Audit Server Operation, класс событий](audit-server-operation-event-class.md)|Указывает на то, что на сервере использованы операции аудита.|  
|[Audit Server Principal Impersonation, класс событий](audit-server-principal-impersonation-event-class.md)|Указывает на то, что в области сервера произошло олицетворение.|  
|[Audit Server Principal Management, класс событий](audit-server-principal-management-event-class.md)|Указывает, что событие CREATE, ALTER или DROP произошло в отношении основного сервера.|  
|[Audit Server Scope GDR, класс событий](audit-server-scope-gdr-event-class.md)|Указывает, что произошло событие GDR для разрешений сервера.|  
|[Audit Server Starts and Stops, класс событий](audit-server-starts-and-stops-event-class.md)|Указывает, что изменено состояние службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Audit Statement Permission, класс событий](audit-statement-permission-event-class.md)|Указывает, что было использовано разрешение на инструкцию.|  
  
## <a name="related-content"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)  
  
  
