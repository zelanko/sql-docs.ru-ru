---
title: "ОТЗЫВ разрешений компонента Service Broker (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- routes [Service Broker], permissions
- Service Broker, permissions
- remote service bindings [Service Broker], permissions
- permissions [Service Broker]
- message types [Service Broker], permissions
- contracts [Service Broker], permissions
- services [Service Broker], permissions
- REVOKE statement, Service Broker
ms.assetid: 70f1d938-97e2-48a4-9bc0-8be9f2f2c36d
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 077fe296f48de1658a56d0c3e7403904652603bc
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="revoke-service-broker-permissions-transact-sql"></a>REVOKE, отмена разрешений для компонента Service Broker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отменяет разрешения по контрактам, типам сообщений, привязкам удаленных служб, маршрутам или службе компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] ON  
    {   
       [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
        }  
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 GRANT OPTION FOR  
 Показывает, что будет отменено право предоставления определенного разрешения остальным участникам. Само разрешение отменено не будет.  
  
> [!IMPORTANT]  
>  Если участник обладает указанным разрешением без параметра GRANT, будет отменено само разрешение.  
  
 *разрешение*  
 Указывает разрешение, которое может быть отменено для защищаемого объекта компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 КОНТРАКТ **::***contract_name*  
 Указывает контракт, для которого отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 Тип сообщения **::***message_type_name*  
 Указывает тип сообщения, для которого отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 REMOTE SERVICE BINDING **::***remote_binding_name*  
 Указывает привязку удаленной службы, для которой отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 МАРШРУТ **::***route_name*  
 Указывает маршрут, для которого отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 Служба **::***message_type_name*  
 Указывает службу, для которой отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 *database_principal*  
 Задает участника, у которого отменяется разрешение. *database_principal* может принимать одно из следующих действий:  
  
-   Пользователь базы данных  
  
-   Роль базы данных  
  
-   Роль приложения  
  
-   Пользователь базы данных, сопоставленный имени входа Windows  
  
-   Пользователь базы данных, сопоставленный группе Windows  
  
-   Пользователь базы данных, сопоставленный сертификату  
  
-   Пользователь базы данных, сопоставленный асимметричному ключу  
  
-   Пользователь базы данных, не сопоставленный серверу-участнику  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS *revoking_principal*  
 Указывает участника, от которого участник, выполняющий данный запрос, получает право на отмену разрешения. *revoking_principal* может принимать одно из следующих действий:  
  
-   Пользователь базы данных  
  
-   Роль базы данных  
  
-   Роль приложения  
  
-   Пользователь базы данных, сопоставленный имени входа Windows  
  
-   Пользователь базы данных, сопоставленный группе Windows  
  
-   Пользователь базы данных, сопоставленный сертификату  
  
-   Пользователь базы данных, сопоставленный асимметричному ключу  
  
-   Пользователь базы данных, не сопоставленный серверу-участнику  
  
## <a name="remarks"></a>Замечания  
  
## <a name="service-broker-contracts"></a>Контракты компонента Service Broker  
 Контракт компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является для него родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые могут быть отменены для [!INCLUDE[ssSB](../../includes/sssb-md.md)] контракта, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение контракта компонента Service Broker|Содержится в разрешении контракта компонента Service Broker|Содержится в разрешении базы данных|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Типы сообщений компонента Service Broker  
 Тип сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее конкретные и ограниченные разрешения, которые могут быть отменены для типа сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], перечислены в следующей таблице наряду с более общими разрешениями, содержащими их неявно.  
  
|Разрешение типа сообщений компонента Service Broker|Содержится в разрешении типа сообщений компонента Service Broker|Содержится в разрешении базы данных|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Привязки удаленной службы компонента Service Broker  
 Привязка удаленной службы компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее конкретные и ограниченные разрешения, которые могут быть отменены для привязки удаленной службы компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], перечислены в следующей таблице наряду с более общими разрешениями, содержащими их неявно.  
  
|Разрешение привязки удаленной службы компонента Service Broker|Содержится в разрешении привязки удаленной службы компонента Service Broker|Содержится в разрешении базы данных|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Маршруты компонента Service Broker  
 Маршрут компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые могут быть отменены для [!INCLUDE[ssSB](../../includes/sssb-md.md)] маршрута, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение маршрута компонента Service Broker|Содержится в разрешении маршрута компонента Service Broker|Содержится в разрешении базы данных|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Службы компонента Service Broker  
 Служба компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые могут быть отменены для [!INCLUDE[ssSB](../../includes/sssb-md.md)] службы, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение службы компонента Service Broker|Содержится в разрешении службы компонента Service Broker|Содержится в разрешении базы данных|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CONTROL на контракт, тип сообщений, привязки удаленной службы, маршрут или службу компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Разрешения GRANT службы Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)   
 [ЗАПРЕТ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
