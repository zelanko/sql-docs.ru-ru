---
title: "Категория событий Security Audit (приложение SQL Server Profiler) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [SQL Server], Security Audit event category
- SQL Server event classes, Security Audit event category
ms.assetid: e64f7695-2f23-4adb-b83d-52f147cc1a2f
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: eb5a25cf31ddd1581f2e0954d4b7fb78689fa115
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="security-audit-event-category-sql-server-profiler"></a>Категория событий Security Audit (приложение SQL Server Profiler)
  Категория событий **Security Audit** включает в себя события аудита безопасности.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Audit Add DB User](../../relational-databases/event-classes/audit-add-db-user-event-class.md)|Указывает, что имя входа пользователя базы данных было добавлено или удалено из базы данных.|  
|[Класс событий Audit Add Login to Server Role](../../relational-databases/event-classes/audit-add-login-to-server-role-event-class.md)|Указывает, что имя входа было добавлено или удалено из предопределенной роли сервера.|  
|[Класс событий Audit Add Member to DB Role](../../relational-databases/event-classes/audit-add-member-to-db-role-event-class.md)|Указывает, что имя входа было добавлено или удалено из роли.|  
|[Класс событий Audit Add Role](../../relational-databases/event-classes/audit-add-role-event-class.md)|Указывает, что роль базы данных была добавлена или удалена из базы данных.|  
|[Класс событий Audit Addlogin](../../relational-databases/event-classes/audit-addlogin-event-class.md)|Указывает, что имя входа было добавлено или удалено.|  
|[Класс событий Audit App Role Change Password](../../relational-databases/event-classes/audit-app-role-change-password-event-class.md)|Указывает, что пароль для роли приложения был изменен.|  
|[Класс событий Audit Backup и Restore](../../relational-databases/event-classes/audit-backup-and-restore-event-class.md)|Указывает, что была выполнена инструкция по восстановлению или резервному копированию.|  
|[Класс событий Audit Broker Conversation](../../relational-databases/event-classes/audit-broker-conversation-event-class.md)|Уведомляет о сообщениях аудита, относящихся к безопасности диалога компонента Service Broker.|  
|[Класс событий Audit Broker Login](../../relational-databases/event-classes/audit-broker-login-event-class.md)|Уведомляет о сообщениях аудита, относящихся к транспортной безопасности компонента Service Broker.|  
|[Класс событий Audit Change Audit](../../relational-databases/event-classes/audit-change-audit-event-class.md)|Указывает, что были внесены изменения в трассировку аудита.|  
|[Класс событий Audit Change Database Owner](../../relational-databases/event-classes/audit-change-database-owner-event-class.md)|Указывает, что разрешения на изменение владельца базы данных были проверены.|  
|[Класс событий Audit Database Management](../../relational-databases/event-classes/audit-database-management-event-class.md)|Указывает, что база данных была создана, изменена или удалена.|  
|[Класс событий Audit Database Mirroring Login](../../relational-databases/event-classes/audit-database-mirroring-login-event-class.md)|Уведомляет о сообщениях аудита, относящихся к транспортной безопасности зеркального отображения базы данных.|  
|[Класс событий Audit Database Object Access](../../relational-databases/event-classes/audit-database-object-access-event-class.md)|Указывает, что был получен доступ к объекту базы данных, например схеме.|  
|[Класс событий Audit Database Object GDR](../../relational-databases/event-classes/audit-database-object-gdr-event-class.md)|Указывает, что произошло событие GDR для объекта базы данных.|  
|[Класс событий Audit Database Object Management](../../relational-databases/event-classes/audit-database-object-management-event-class.md)|Указывает, что инструкция CREATE, ALTER или DROP была выполнена в отношении объекта базы данных.|  
|[Класс событий Audit Database Object Take Ownership](../../relational-databases/event-classes/audit-database-object-take-ownership-event-class.md)|Указывает, что в области базы данных произошло изменение владельца объектов.|  
|[Класс событий Audit Database Operation](../../relational-databases/event-classes/audit-database-operation-event-class.md)|Указывает, что выполнена одна из операций, таких как уведомление запроса контрольной точки или подписки.|  
|[Класс событий Audit Database Principal Impersonation](../../relational-databases/event-classes/audit-database-principal-impersonation-event-class.md)|Указывает на то, что в области базы данных произошло олицетворение.|  
|[Класс событий Audit Database Principal Management](../../relational-databases/event-classes/audit-database-principal-management-event-class.md)|Указывает, что участники были созданы, изменены или удалены из базы данных.|  
|[Класс событий Audit Database Scope GDR](../../relational-databases/event-classes/audit-database-scope-gdr-event-class.md)|Указывает на выполнение пользователем [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]инструкции GRANT, REVOKE или DENY.|  
|[Класс событий Audit DBCC](../../relational-databases/event-classes/audit-dbcc-event-class.md)|Указывает, что была выполнена команда DBCC.|  
|[Класс событий Audit Fulltext](../../relational-databases/event-classes/audit-fulltext-event-class.md)|Указывает, что произошло полнотекстовое событие.|  
|[Класс событий Audit Login Change Password](../../relational-databases/event-classes/audit-login-change-password-event-class.md)|Указывает, что пользователь изменил пароль, используемый для входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Класс событий Audit Login Change Property](../../relational-databases/event-classes/audit-login-change-property-event-class.md)|Указывает, что для изменения свойства имени входа была использована хранимая процедура **sp_defaultdb**, **sp_defaultlanguage**или инструкция ALTER LOGIN.|  
|[Класс событий Audit Login](../../relational-databases/event-classes/audit-login-event-class.md)|Указывает, что пользователь успешно выполнил вход на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Класс событий Audit Login Failed](../../relational-databases/event-classes/audit-login-failed-event-class.md)|Указывает, что пользователь выполнил попытку входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая завершилась неудачно.|  
|[Класс событий Audit Login GDR](../../relational-databases/event-classes/audit-login-gdr-event-class.md)|Указывает, что право входа в систему [!INCLUDE[msCoName](../../includes/msconame-md.md)] было добавлено или удалено.|  
|[Класс событий Audit Logout](../../relational-databases/event-classes/audit-logout-event-class.md)|Указывает, что пользователь вышел из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Класс событий Audit Object Derived Permission](../../relational-databases/event-classes/audit-object-derived-permission-event-class.md)|Указывает, что инструкция CREATE, ALTER или DROP была выполнена в отношении объекта.|  
|[Класс событий Audit Schema Object Access](../../relational-databases/event-classes/audit-schema-object-access-event-class.md)|Указывает, что было использовано разрешение объекта (такое как SELECT).|  
|[Класс событий Audit Schema Object GDR](../../relational-databases/event-classes/audit-schema-object-gdr-event-class.md)|Указывает на выполнение пользователем инструкции GRANT, REVOKE или DENY по поводу разрешения для объекта схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Класс событий Audit Schema Object Management](../../relational-databases/event-classes/audit-schema-object-management-event-class.md)|Указывает, что объект сервера был создан, изменен или удален.|  
|[Класс событий Audit Schema Object Take Ownership](../../relational-databases/event-classes/audit-schema-object-take-ownership-event-class.md)|Указывает, что была выполнена проверка разрешений на изменение владельца объекта схемы.|  
|[Класс событий Audit Server Alter Trace](../../relational-databases/event-classes/audit-server-alter-trace-event-class.md)|Указывает, что была выполнена проверка разрешения ALTER TRACE.|  
|[Класс событий Audit Server Object GDR](../../relational-databases/event-classes/audit-server-object-gdr-event-class.md)|Указывает, что произошло событие GDR для объекта схемы.|  
|[Класс событий Audit Server Object Management](../../relational-databases/event-classes/audit-server-object-management-event-class.md)|Указывает, что событие CREATE, ALTER или DROP произошло в отношении объекта сервера.|  
|[Класс событий Audit Server Object Take Ownership](../../relational-databases/event-classes/audit-server-object-take-ownership-event-class.md)|Указывает, что изменен владелец объекта сервера.|  
|[Класс событий Audit Server Operation](../../relational-databases/event-classes/audit-server-operation-event-class.md)|Указывает на то, что на сервере использованы операции аудита.|  
|[Класс событий Audit Server Principal Impersonation](../../relational-databases/event-classes/audit-server-principal-impersonation-event-class.md)|Указывает на то, что в области сервера произошло олицетворение.|  
|[Класс событий Audit Server Principal Management](../../relational-databases/event-classes/audit-server-principal-management-event-class.md)|Указывает, что событие CREATE, ALTER или DROP произошло в отношении основного сервера.|  
|[Класс событий Audit Server Scope GDR](../../relational-databases/event-classes/audit-server-scope-gdr-event-class.md)|Указывает, что произошло событие GDR для разрешений сервера.|  
|[Класс событий Audit Server Starts and Stops](../../relational-databases/event-classes/audit-server-starts-and-stops-event-class.md)|Указывает, что изменено состояние службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Класс событий Audit Statement Permission](../../relational-databases/event-classes/audit-statement-permission-event-class.md)|Указывает, что было использовано разрешение на инструкцию.|  
  
## <a name="related-content"></a>См. также  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
