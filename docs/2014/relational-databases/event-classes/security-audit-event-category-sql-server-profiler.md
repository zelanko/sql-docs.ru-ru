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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63044226"
---
# <a name="security-audit-event-category-sql-server-profiler"></a>Категория событий Security Audit (приложение SQL Server Profiler)
  Категория событий **Security Audit** включает в себя события аудита безопасности.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Класс событий Audit Add DB User](audit-add-db-user-event-class.md)|Указывает, что имя входа пользователя базы данных было добавлено или удалено из базы данных.|  
|[Класс событий Audit Add Login to Server Role](audit-add-login-to-server-role-event-class.md)|Указывает, что имя входа было добавлено или удалено из предопределенной роли сервера.|  
|[Класс событий Audit Add Member to DB Role](audit-add-member-to-db-role-event-class.md)|Указывает, что имя входа было добавлено или удалено из роли.|  
|[Класс событий Audit Add Role](audit-add-role-event-class.md)|Указывает, что роль базы данных была добавлена или удалена из базы данных.|  
|[Класс событий Audit Addlogin](audit-addlogin-event-class.md)|Указывает, что имя входа было добавлено или удалено.|  
|[Класс событий Audit App Role Change Password](audit-app-role-change-password-event-class.md)|Указывает, что пароль для роли приложения был изменен.|  
|[Класс событий Audit Backup и Restore](audit-backup-and-restore-event-class.md)|Указывает, что была выполнена инструкция по восстановлению или резервному копированию.|  
|[Класс событий Audit Broker Conversation](broker-conversation-event-class.md)|Уведомляет о сообщениях аудита, относящихся к безопасности диалога компонента Service Broker.|  
|[Класс событий Audit Broker Login](audit-broker-login-event-class.md)|Уведомляет о сообщениях аудита, относящихся к транспортной безопасности компонента Service Broker.|  
|[Класс событий Audit Change Audit](audit-change-audit-event-class.md)|Указывает, что были внесены изменения в трассировку аудита.|  
|[Класс событий Audit Change Database Owner](audit-change-database-owner-event-class.md)|Указывает, что разрешения на изменение владельца базы данных были проверены.|  
|[Класс событий Audit Database Management](audit-database-management-event-class.md)|Указывает, что база данных была создана, изменена или удалена.|  
|[Класс событий Audit Database Mirroring Login](audit-database-mirroring-login-event-class.md)|Уведомляет о сообщениях аудита, относящихся к транспортной безопасности зеркального отображения базы данных.|  
|[Класс событий Audit Database Object Access](audit-database-object-access-event-class.md)|Указывает, что был получен доступ к объекту базы данных, например схеме.|  
|[Класс событий Audit Database Object GDR](audit-database-object-gdr-event-class.md)|Указывает, что произошло событие GDR для объекта базы данных.|  
|[Класс событий Audit Database Object Management](audit-database-object-management-event-class.md)|Указывает, что инструкция CREATE, ALTER или DROP была выполнена в отношении объекта базы данных.|  
|[Класс событий Audit Database Object Take Ownership](audit-database-object-take-ownership-event-class.md)|Указывает, что в области базы данных произошло изменение владельца объектов.|  
|[Класс событий Audit Database Operation](audit-database-operation-event-class.md)|Указывает, что выполнена одна из операций, таких как уведомление запроса контрольной точки или подписки.|  
|[Класс событий Audit Database Principal Impersonation](audit-database-principal-impersonation-event-class.md)|Указывает на то, что в области базы данных произошло олицетворение.|  
|[Класс событий Audit Database Principal Management](audit-database-principal-management-event-class.md)|Указывает, что участники были созданы, изменены или удалены из базы данных.|  
|[Класс событий Audit Database Scope GDR](audit-database-scope-gdr-event-class.md)|Указывает на выполнение пользователем [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]инструкции GRANT, REVOKE или DENY.|  
|[Класс событий Audit DBCC](audit-dbcc-event-class.md)|Указывает, что была выполнена команда DBCC.|  
|[Класс событий Audit Fulltext](audit-fulltext-event-class.md)|Указывает, что произошло полнотекстовое событие.|  
|[Класс событий Audit Login Change Password](audit-login-change-password-event-class.md)|Указывает, что пользователь изменил пароль, используемый для входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Класс событий Audit Login Change Property](audit-login-change-property-event-class.md)|Указывает, что для изменения свойства имени входа была использована хранимая процедура **sp_defaultdb**, **sp_defaultlanguage**или инструкция ALTER LOGIN.|  
|[Класс событий Audit Login](audit-login-event-class.md)|Указывает, что пользователь успешно выполнил вход на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Класс событий Audit Login Failed](audit-login-failed-event-class.md)|Указывает, что пользователь выполнил попытку входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая завершилась неудачно.|  
|[Класс событий Audit Login GDR](audit-login-gdr-event-class.md)|Указывает, что право входа в систему [!INCLUDE[msCoName](../../includes/msconame-md.md)] было добавлено или удалено.|  
|[Класс событий Audit Logout](audit-logout-event-class.md)|Указывает, что пользователь вышел из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Класс событий Audit Object Derived Permission](audit-object-derived-permission-event-class.md)|Указывает, что инструкция CREATE, ALTER или DROP была выполнена в отношении объекта.|  
|[Класс событий Audit Schema Object Access](audit-schema-object-access-event-class.md)|Указывает, что было использовано разрешение объекта (такое как SELECT).|  
|[Класс событий Audit Schema Object GDR](audit-schema-object-gdr-event-class.md)|Указывает на выполнение пользователем инструкции GRANT, REVOKE или DENY по поводу разрешения для объекта схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Класс событий Audit Schema Object Management](audit-schema-object-management-event-class.md)|Указывает, что объект сервера был создан, изменен или удален.|  
|[Класс событий Audit Schema Object Take Ownership](audit-schema-object-take-ownership-event-class.md)|Указывает, что была выполнена проверка разрешений на изменение владельца объекта схемы.|  
|[Класс событий Audit Server Alter Trace](audit-server-alter-trace-event-class.md)|Указывает, что была выполнена проверка разрешения ALTER TRACE.|  
|[Класс событий Audit Server Object GDR](audit-server-object-gdr-event-class.md)|Указывает, что произошло событие GDR для объекта схемы.|  
|[Класс событий Audit Server Object Management](audit-server-object-management-event-class.md)|Указывает, что событие CREATE, ALTER или DROP произошло в отношении объекта сервера.|  
|[Класс событий Audit Server Object Take Ownership](audit-server-object-take-ownership-event-class.md)|Указывает, что изменен владелец объекта сервера.|  
|[Класс событий Audit Server Operation](audit-server-operation-event-class.md)|Указывает на то, что на сервере использованы операции аудита.|  
|[Класс событий Audit Server Principal Impersonation](audit-server-principal-impersonation-event-class.md)|Указывает на то, что в области сервера произошло олицетворение.|  
|[Класс событий Audit Server Principal Management](audit-server-principal-management-event-class.md)|Указывает, что событие CREATE, ALTER или DROP произошло в отношении основного сервера.|  
|[Класс событий Audit Server Scope GDR](audit-server-scope-gdr-event-class.md)|Указывает, что произошло событие GDR для разрешений сервера.|  
|[Класс событий Audit Server Starts and Stops](audit-server-starts-and-stops-event-class.md)|Указывает, что изменено состояние службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Класс событий Audit Statement Permission](audit-statement-permission-event-class.md)|Указывает, что было использовано разрешение на инструкцию.|  
  
## <a name="related-content"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)  
  
  
