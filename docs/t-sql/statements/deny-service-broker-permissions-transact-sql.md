---
title: DENY, запрет разрешений для компонента Service Broker (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [Service Broker]
- routes [Service Broker], permissions
- Service Broker, permissions
- DENY statement, Service Broker
- remote service bindings [Service Broker], permissions
- permissions [Service Broker]
- message types [Service Broker], permissions
- denying permissions [SQL Server], Service Broker
- contracts [Service Broker], permissions
- services [Service Broker], permissions
ms.assetid: 7c6de71b-865c-41db-9413-ad9b3562e579
caps.latest.revision: 22
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c5553d6a7ea1f1dc7f241c8e2361e80a601dd706
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785665"
---
# <a name="deny-service-broker-permissions-transact-sql"></a>DENY, запрет разрешений компонента Service Broker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запрещает разрешения по контрактам, типам сообщений, привязкам удаленной службы, маршрутам или службам компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission  [ ,...n ] ON  
    {    
       [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
        }  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *permission*  
 Указывает разрешение, которое может быть запрещено для защищаемых элементов компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Список разрешений см. в подразделе "Примечания" далее в этом разделе.  
  
 CONTRACT **::***contract_name*  
 Указывает контракт, для которого запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 MESSAGE TYPE **::***message_type_name*  
 Указывает тип сообщений, для которого запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 REMOTE SERVICE BINDING **::***remote_binding_name*  
 Указывает привязку удаленной службы, для которой запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 ROUTE **::***route_name*  
 Указывает маршрут, для которого запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 SERVICE **::***message_type_name*  
 Указывает службу, для которой запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 *database_principal*  
 Задает участника, для которого запрещается разрешение. Это может быть:  
  
-   пользователь базы данных;  
-   роль базы данных;  
-   роль приложения;  
-   пользователь базы данных, сопоставленный с именем входа Windows;  
-   пользователь базы данных, сопоставленный с группой Windows;  
-   пользователь базы данных, сопоставленный с сертификатом;  
-   пользователь базы данных, сопоставленный с асимметричным ключом;  
-   пользователь базы данных, не сопоставленный с сервером-участником.  
  
CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
*denying_principal*  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения. Это может быть:  
  
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
 Контракт компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, находящийся в базе данных, которая является родительской в иерархии разрешений. Наиболее конкретные и ограниченные разрешения, которые могут быть отклонены для контракта [!INCLUDE[ssSB](../../includes/sssb-md.md)], а также более общие разрешения, которые неявно содержат эти более конкретные разрешения, указаны в следующей таблице.  
  
|Разрешение контракта компонента Service Broker|Содержится в разрешении контракта компонента Service Broker|Содержится в разрешении базы данных|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Типы сообщений компонента Service Broker  
 Тип сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запретить для типа сообщений компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], перечислены в следующей таблице наряду с более общими разрешениями, неявно их содержащими.  
  
|Разрешение типа сообщений компонента Service Broker|Содержится в разрешении типа сообщений компонента Service Broker|Содержится в разрешении базы данных|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Привязки удаленной службы компонента Service Broker  
 Привязка удаленной службы компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые можно запретить по привязке удаленной службы компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], перечислены в следующей таблице наряду с более общими разрешениями, неявно их содержащими.  
  
|Разрешение привязки удаленной службы компонента Service Broker|Содержится в разрешении привязки удаленной службы компонента Service Broker|Содержится в разрешении базы данных|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Маршруты компонента Service Broker  
 Маршрут компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее конкретные и ограниченные разрешения, которые могут быть отклонены для маршрута [!INCLUDE[ssSB](../../includes/sssb-md.md)], а также более общие разрешения, которые неявно содержат эти более конкретные разрешения, указаны в следующей таблице.  
  
|Разрешение маршрута компонента Service Broker|Содержится в разрешении маршрута компонента Service Broker|Содержится в разрешении базы данных|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Службы компонента Service Broker  
 Служба компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее конкретные и ограниченные разрешения, которые могут быть отклонены для службы [!INCLUDE[ssSB](../../includes/sssb-md.md)], а также более общие разрешения, которые неявно содержат эти более конкретные разрешения, указаны в следующей таблице.  
  
|Разрешение службы компонента Service Broker|Содержится в разрешении службы компонента Service Broker|Содержится в разрешении базы данных|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL по контрактам, типам сообщений, привязкам удаленной службы, маршрутам или службам компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. При использовании предложения AS указанный участник должен быть владельцем защищаемого объекта, разрешения на который для него запрещаются.  
  
## <a name="see-also"></a>См. также:  
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [REVOKE, запрет разрешений на Service Broker (Transact-SQL)](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)  
  
  
