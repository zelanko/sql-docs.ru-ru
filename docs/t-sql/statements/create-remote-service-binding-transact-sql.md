---
title: "СОЗДАЙТЕ ПРИВЯЗКУ УДАЛЕННОЙ службы (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
f1_keywords:
- CREATE REMOTE SERVICE BINDING
- SERVICE_BINDING_TSQL
- CREATE REMOTE SERVICE
- REMOTE_TSQL
- CREATE_REMOTE_SERVICE_BINDING_TSQL
- CREATE_REMOTE_SERVICE_TSQL
- BINDING
- SERVICE BINDING
- BINDING_TSQL
- CREATE_REMOTE_TSQL
- REMOTE_SERVICE_TSQL
- CREATE REMOTE
- REMOTE SERVICE
- REMOTE_SERVICE_BINDING_TSQL
- REMOTE
- REMOTE SERVICE BINDING
dev_langs:
- TSQL
helpviewer_keywords:
- binding remote service [Service Broker]
- dialog security [Service Broker]
- end-to-end security [Service Broker]
- security [Service Broker], remote service bindings
- CREATE REMOTE SERVICE BINDING statement
- conversation security [Service Broker]
- remote service bindings [Service Broker], creating
ms.assetid: 4165c404-4d50-4063-9a6e-6e267d309376
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f0df6ec364331c118de08b6eb312d9cf331761e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="create-remote-service-binding-transact-sql"></a>CREATE REMOTE SERVICE BINDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает привязку, определяющую учетные данные безопасности, которые используются при создании диалога с удаленной службой.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE REMOTE SERVICE BINDING binding_name   
   [ AUTHORIZATION owner_name ]   
   TO SERVICE 'service_name'   
   WITH  USER = user_name [ , ANONYMOUS = { ON | OFF } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *binding_name*  
 Имя создаваемой привязки удаленной службы. Не могут быть указаны имена сервера, базы данных и схемы. *Binding_name* должен быть допустимым **sysname**.  
  
 АВТОРИЗАЦИЯ *owner_name*  
 Назначает владельцем привязки указанного пользователя или роль базы данных. Если текущий пользователь является **dbo** или **sa**, *owner_name* может быть именем любого допустимого пользователя или роли. В противном случае *owner_name* должен быть именем текущего пользователя, имя пользователя, у которого у текущего пользователя есть разрешение IMPERSONATE для или имя роли, к которой принадлежит текущий пользователь.  
  
 СЛУЖБЕ "*service_name*"  
 Указывает удаленную службу, которую необходимо привязать к пользователю, указанному в предложении WITH USER.  
  
 ПОЛЬЗОВАТЕЛЬ = *имя_пользователя*  
 Указывает участника базы данных, владеющего сертификатом, который связан с удаленной службой, указываемой предложением TO SERVICE. Этот сертификат применяется для шифрования и проверки подлинности сообщений, обмен которыми производится с удаленной службой.  
  
 ANONYMOUS  
 Указывает, используется ли анонимная проверка подлинности при связи с удаленной службой. При настройке ANONYMOUS = ON, используется анонимная проверка подлинности и операции в удаленной базе данных выполняются от имени является членом **открытый** предопределенной роли базы данных. Если ANONYMOUS = OFF, операции в удаленной базе данных выполняются от имени определенного пользователя этой базы данных. Если это выражение не задано, по умолчанию параметр принимает значение OFF.  
  
## <a name="remarks"></a>Замечания  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует привязку удаленной службы для поиска сертификата, который будет применяться при создании новых диалогов. Открытый ключ в сертификат, связанный с *имя_пользователя* используется для проверки подлинности сообщений, отправленных удаленной службы и для шифрования сеансового ключа, который затем используется для шифрования сообщений. Сертификат для *имя_пользователя* сертификат для пользователя в базе данных, на котором находится удаленная служба, должен соответствовать.  
  
 Привязка удаленной службы необходима только для служб вызывающей стороны, которые взаимодействуют с конечными службами за пределами экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. База данных, в которой находится служба вызывающей стороны, должна содержать привязки удаленных служб для всех целевых служб за пределами экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Базе данных, на которой находится конечная служба, нет необходимости хранить привязки для всех служб вызывающей стороны, которые с ней взаимодействуют. Если инициатор и целевая служба находятся на одном и том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], привязки удаленной службы не нужны. Тем не менее если привязка удаленной службы присутствует где *service_name* указанное для службы совпадает с именем локальной службы, [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует эту привязку.  
  
 Если ANONYMOUS = ON, служба вызывающей стороны подключается к целевой службе как член **открытый** предопределенной роли базы данных. По умолчанию члены этой роли не имеют разрешения на подключение к базе данных. Для успешной отправки сообщения, необходимо предоставить в целевую базу данных **открытый** роли разрешение CONNECT для базы данных и разрешение SEND для целевой службы.  
  
 Если пользователю принадлежит более одного сертификата, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] выбирает из действующих и помеченных как AVAILABLE FOR BEGIN_DIALOG сертификатов тот, который имеет больший срок действия.  
  
## <a name="permissions"></a>Permissions  
 Разрешения для создания удаленной службы привязки по умолчанию для пользователя, указанного в предложении USER члены **db_owner** предопределенной роли базы данных, члены **db_ddladmin** фиксированной роли базы данных и члены из **sysadmin** предопределенной роли сервера.  
  
 Пользователь, выполняющий инструкцию CREATE REMOTE SERVICE BINDING, должен иметь разрешение на олицетворение указанного в инструкции участника.  
  
 Привязка удаленной службы не может быть временным объектом. Имена привязок удаленной службы, начиная с версии  **#**  разрешены, но являются постоянными объектами.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-remote-service-binding"></a>A. Создание привязки удаленной службы  
 В следующем примере создается привязка к службе `//Adventure-Works.com/services/AccountsPayable`. Компонент[!INCLUDE[ssSB](../../includes/sssb-md.md)] использует сертификат, принадлежащий участнику базы данных `APUser`, для проверки подлинности удаленной службы и обмена с ней ключами сеанса.  
  
```  
CREATE REMOTE SERVICE BINDING APBinding  
    TO SERVICE '//Adventure-Works.com/services/AccountsPayable'  
    WITH USER = APUser ;  
```  
  
### <a name="b-creating-a-remote-service-binding-using-anonymous-authentication"></a>Б. Создание привязки удаленной службы при использовании анонимной проверки подлинности  
 В следующем примере создается привязка к службе `//Adventure-Works.com/services/AccountsPayable`. Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует сертификат, принадлежащий участнику базы данных `APUser`, для обмена с удаленной службой ключами сеанса. Проверка подлинности при доступе к удаленной службе не производится. В базе данных, на котором находится удаленная служба, сообщения доставляются как **гостевой** пользователя.  
  
```  
CREATE REMOTE SERVICE BINDING APBinding  
    TO SERVICE '//Adventure-Works.com/services/AccountsPayable'  
    WITH USER = APUser, ANONYMOUS=ON ;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER ПРИВЯЗКИ УДАЛЕННОЙ службы &#40; Transact-SQL &#41;](../../t-sql/statements/alter-remote-service-binding-transact-sql.md)   
 [Удаление ПРИВЯЗКИ УДАЛЕННОЙ службы &#40; Transact-SQL &#41;](../../t-sql/statements/drop-remote-service-binding-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
