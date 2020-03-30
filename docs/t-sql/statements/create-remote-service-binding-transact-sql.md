---
title: CREATE REMOTE SERVICE BINDING (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 2fc021cec09a7f62d05f5e435db9d6fc2597fce3
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68117340"
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
 Имя создаваемой привязки удаленной службы. Не могут быть указаны имена сервера, базы данных и схемы. Аргумент *binding_name* должен быть допустимым аргументом **sysname**.  
  
 AUTHORIZATION *owner_name*  
 Назначает владельцем привязки указанного пользователя или роль базы данных. Если текущим пользователем является **dbo** или **sa**, то аргумент *owner_name* может быть именем любого допустимого пользователя или роли. В противном случае аргумент *owner_name* должен быть именем текущего пользователя, именем пользователя, для которого у текущего пользователя есть разрешение IMPERSONATE, или именем роли, которой принадлежит текущий пользователь.  
  
 TO SERVICE '*service_name*'  
 Указывает удаленную службу, которую необходимо привязать к пользователю, указанному в предложении WITH USER.  
  
 USER = *user_name*  
 Указывает участника базы данных, владеющего сертификатом, который связан с удаленной службой, указываемой предложением TO SERVICE. Этот сертификат применяется для шифрования и проверки подлинности сообщений, обмен которыми производится с удаленной службой.  
  
 ANONYMOUS  
 Указывает, используется ли анонимная проверка подлинности при связи с удаленной службой. Если ANONYMOUS = ON, используется анонимная проверка подлинности и все операции в удаленной базе данных выполняются от имени члена предопределенной роли базы данных **public**. Если ANONYMOUS = OFF, операции в удаленной базе данных выполняются от имени определенного пользователя этой базы данных. Если это выражение не задано, по умолчанию параметр принимает значение OFF.  
  
## <a name="remarks"></a>Remarks  
 Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует привязку удаленной службы для поиска сертификата, который будет применяться при создании новых диалогов. Открытый ключ в сертификате, связанный с пользователем *user_name*, используется для проверки подлинности сообщений, отправляемых в удаленную службу, и для шифрования сеансового ключа, который затем используется для шифрования сеанса связи. Сертификат для пользователя *user_name* должен соответствовать сертификату для пользователя в базе данных, в которой находится удаленная служба.  
  
 Привязка удаленной службы необходима только для служб вызывающей стороны, которые взаимодействуют с конечными службами за пределами экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. База данных, в которой находится служба вызывающей стороны, должна содержать привязки удаленных служб для всех целевых служб за пределами экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Базе данных, на которой находится конечная служба, нет необходимости хранить привязки для всех служб вызывающей стороны, которые с ней взаимодействуют. Если инициатор и целевая служба находятся на одном и том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], привязки удаленной службы не нужны. Однако если привязка удаленной службы существует в случае, когда для параметра TO SERVICE было указано имя *service_name*, совпадающее с именем локальной службы, то [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует эту привязку.  
  
 Если ANONYMOUS = ON, служба вызывающей стороны подключается к конечной службе как член предопределенной роли базы данных **public**. По умолчанию члены этой роли не имеют разрешения на подключение к базе данных. Для успешной отправки сообщения целевая база данных должна предоставить роли **public** разрешение CONNECT для базы данных и разрешение SEND для конечной службы.  
  
 Если пользователю принадлежит более одного сертификата, компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] выбирает из действующих и помеченных как AVAILABLE FOR BEGIN_DIALOG сертификатов тот, который имеет больший срок действия.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на создание привязки удаленной службы по умолчанию даются пользователю, имя которого указано в предложении USER, членам предопределенных ролей базы данных **db_owner** и **db_ddladmin** и членам предопределенной роли сервера **sysadmin**.  
  
 Пользователь, выполняющий инструкцию CREATE REMOTE SERVICE BINDING, должен иметь разрешение на олицетворение указанного в инструкции участника.  
  
 Привязка удаленной службы не может быть временным объектом. Имена привязок удаленной службы, начинающиеся с символа **#** , допустимы, но они являются постоянными объектами.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-remote-service-binding"></a>A. Создание привязки удаленной службы  
 В следующем примере создается привязка к службе `//Adventure-Works.com/services/AccountsPayable`. Компонент[!INCLUDE[ssSB](../../includes/sssb-md.md)] использует сертификат, принадлежащий участнику базы данных `APUser`, для проверки подлинности удаленной службы и обмена с ней ключами сеанса.  
  
```  
CREATE REMOTE SERVICE BINDING APBinding  
    TO SERVICE '//Adventure-Works.com/services/AccountsPayable'  
    WITH USER = APUser ;  
```  
  
### <a name="b-creating-a-remote-service-binding-using-anonymous-authentication"></a>Б. Создание привязки удаленной службы при использовании анонимной проверки подлинности  
 В следующем примере создается привязка к службе `//Adventure-Works.com/services/AccountsPayable`. Компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] использует сертификат, принадлежащий участнику базы данных `APUser`, для обмена с удаленной службой ключами сеанса. Проверка подлинности при доступе к удаленной службе не производится. В базе данных, в которой находится удаленная служба, сообщения доставляются от имени пользователя **guest**.  
  
```  
CREATE REMOTE SERVICE BINDING APBinding  
    TO SERVICE '//Adventure-Works.com/services/AccountsPayable'  
    WITH USER = APUser, ANONYMOUS=ON ;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER REMOTE SERVICE BINDING (Transact-SQL)](../../t-sql/statements/alter-remote-service-binding-transact-sql.md)   
 [DROP REMOTE SERVICE BINDING (Transact-SQL)](../../t-sql/statements/drop-remote-service-binding-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
