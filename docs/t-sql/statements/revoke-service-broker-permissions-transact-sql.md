---
title: REVOKE, отмена разрешений для компонента Service Broker (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4ed6e67bbf6f3fcda872650c2d3394d6311802b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67914219"
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
  
 *permission*  
 Указывает разрешение, которое может быть отменено для защищаемого объекта компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 CONTRACT **::** _contract_name_  
 Указывает контракт, для которого отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 MESSAGE TYPE **::** _message_type_name_  
 Указывает тип сообщения, для которого отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 REMOTE SERVICE BINDING **::** _remote_binding_name_  
 Указывает привязку удаленной службы, для которой отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 ROUTE **::** _route_name_  
 Указывает маршрут, для которого отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 SERVICE **::** _message_type_name_  
 Указывает службу, для которой отменяется разрешение. Квалификатор области **::** является обязательным.  
  
 *database_principal*  
 Задает участника, у которого отменяется разрешение. *database_principal* может быть одним из следующих:  
  
-   пользователь базы данных;  
  
-   роль базы данных;  
  
-   роль приложения;  
  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
  
-   пользователь базы данных, сопоставленный с группой Windows;  
  
-   пользователь базы данных, сопоставленный с сертификатом;  
  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
  
-   пользователь базы данных, не сопоставленный с сервером-участником.  
  
 CASCADE  
 Показывает, что отменяемое разрешение также отменяется для других участников, для которых оно было предоставлено или запрещено данным участником.  
  
> [!CAUTION]  
>  Каскадная отмена разрешения, предоставленного с помощью параметра WITH GRANT OPTION, приведет к отмене разрешений GRANT и DENY для этого разрешения.  
  
 AS *revoking_principal*  
 Указывает участника, от которого участник, выполняющий данный запрос, получает право на отмену разрешения. В качестве *участника_дающего_право_на_отмену_разрешения* может быть указан один из следующих участников:  
  
-   пользователь базы данных;  
  
-   роль базы данных;  
  
-   роль приложения;  
  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
  
-   пользователь базы данных, сопоставленный с группой Windows;  
  
-   пользователь базы данных, сопоставленный с сертификатом;  
  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
  
-   пользователь базы данных, не сопоставленный с сервером-участником.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="service-broker-contracts"></a>Контракты компонента Service Broker  
 Контракт компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является для него родительской в иерархии разрешений. Наиболее конкретные и ограниченные разрешения, которые могут быть отменены для контракта [!INCLUDE[ssSB](../../includes/sssb-md.md)], а также более общие разрешения, которые неявно содержат эти более конкретные разрешения, указаны в следующей таблице.  
  
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
 Маршрут компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее конкретные и ограниченные разрешения, которые могут быть отменены для маршрута [!INCLUDE[ssSB](../../includes/sssb-md.md)], а также более общие разрешения, которые неявно содержат эти более конкретные разрешения, указаны в следующей таблице.  
  
|Разрешение маршрута компонента Service Broker|Содержится в разрешении маршрута компонента Service Broker|Содержится в разрешении базы данных|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Службы компонента Service Broker  
 Служба компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее конкретные и ограниченные разрешения, которые могут быть отменены для службы [!INCLUDE[ssSB](../../includes/sssb-md.md)], а также более общие разрешения, которые неявно содержат эти более конкретные разрешения, указаны в следующей таблице.  
  
|Разрешение службы компонента Service Broker|Содержится в разрешении службы компонента Service Broker|Содержится в разрешении базы данных|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL на контракт, тип сообщений, привязки удаленной службы, маршрут или службу компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [GRANT, предоставление разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)   
 [DENY, запрет разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
