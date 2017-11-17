---
title: "ЗАПРЕТ разрешений компонента Service Broker (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ed0ab0e375ecddbf9086647adce744a8ef4cb53d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

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
 *разрешение*  
 Указывает разрешение, которое может быть запрещено для защищаемых элементов компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 КОНТРАКТ **::***contract_name*  
 Указывает контракт, для которого запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 Тип сообщения **::***message_type_name*  
 Указывает тип сообщений, для которого запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 REMOTE SERVICE BINDING **::***remote_binding_name*  
 Указывает привязку удаленной службы, для которой запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 МАРШРУТ **::***route_name*  
 Указывает маршрут, для которого запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 Служба **::***message_type_name*  
 Указывает службу, для которой запрещено разрешение. Квалификатор области **::** является обязательным.  
  
 *database_principal*  
 Задает участника, для которого запрещается разрешение, — Это может быть:  
  
-   Пользователь базы данных  
-   Роль базы данных  
-   Роль приложения  
-   Пользователь базы данных, сопоставленный имени входа Windows  
-   Пользователь базы данных, сопоставленный группе Windows  
-   Пользователь базы данных, сопоставленный сертификату  
-   Пользователь базы данных, сопоставленный асимметричному ключу  
-   Пользователь базы данных, не сопоставленный серверу-участнику  
  
CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
*denying_principal*  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения. Это может быть:  
  
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
 Контракт компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, находящийся в базе данных, которая является родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые могут быть запрещены на [!INCLUDE[ssSB](../../includes/sssb-md.md)] контракта, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
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
 Маршрут компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые могут быть запрещены на [!INCLUDE[ssSB](../../includes/sssb-md.md)] маршрута, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение маршрута компонента Service Broker|Содержится в разрешении маршрута компонента Service Broker|Содержится в разрешении базы данных|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Службы компонента Service Broker  
 Служба компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)] — это защищаемый объект уровня базы данных, содержащийся в базе данных, которая является родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения, которые могут быть запрещены на [!INCLUDE[ssSB](../../includes/sssb-md.md)] службы, перечислены в следующей таблице вместе с более общими разрешениями, неявно их содержащими.  
  
|Разрешение службы компонента Service Broker|Содержится в разрешении службы компонента Service Broker|Содержится в разрешении базы данных|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CONTROL по контрактам, типам сообщений, привязкам удаленной службы, маршрутам или службам компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)]. При использовании предложения AS указанный участник должен быть владельцем защищаемого объекта, разрешения на который для него запрещаются.  
  
## <a name="see-also"></a>См. также:  
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [ОТЗЫВ разрешений компонента Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [Разрешения &#40; компонент Database Engine &#41;](../../relational-databases/security/permissions-database-engine.md)  
  
  

