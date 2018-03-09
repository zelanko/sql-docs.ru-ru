---
title: "ALTER BROKER PRIORITY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- ALTER_BROKER_TSQL
- ALTER BROKER PRIORITY
- ALTER BROKER
- ALTER_BROKER_PRIORITY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER BROKER PRIORITY statement
- ssbdiagnose
ms.assetid: 15fda1b2-e4dd-4f9d-935a-2e38926075b2
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 833c0bed38d02905b3a260f50824825c9859484f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="alter-broker-priority-transact-sql"></a>Инструкция ALTER BROKER PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет свойства приоритета диалога компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER BROKER PRIORITY ConversationPriorityName  
FOR CONVERSATION  
{ SET ( [ CONTRACT_NAME = {ContractName | ANY } ]  
        [ [ , ] LOCAL_SERVICE_NAME = {LocalServiceName | ANY } ]  
        [ [ , ] REMOTE_SERVICE_NAME = {'RemoteServiceName' | ANY } ]  
        [ [ , ] PRIORITY_LEVEL = { PriorityValue | DEFAULT } ]  
              )  
}  
[;]  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConversationPriorityName*  
 Имя изменяемого приоритета диалога. Это имя должно ссылаться на приоритет диалога в текущей базе данных.  
  
 SET  
 Задает критерий для определения применимости приоритета к заданному диалогу. SET является обязательным и должен содержать хотя бы один критерий: CONTRACT_NAME, LOCAL_SERVICE_NAME, REMOTE_SERVICE_NAME или параметра PRIORITY_LEVEL.  
  
 CONTRACT_NAME = {*ContractName* | **ANY**}  
 Указывает имя контракта, который будет использоваться в качестве критерия, определяющего применимость приоритета к диалогу. *ContractName* — [!INCLUDE[ssDE](../../includes/ssde-md.md)] идентификатор и необходимо указать имя контракта в текущей базе данных.  
  
 *ContractName*  
 Указывает, что приоритет диалога может применяться только к диалогам, где в инструкции BEGIN DIALOG, в которой начала диалог параметр ON CONTRACT *ContractName*.  
  
 ANY  
 Указывает, что приоритет может применяться к любому диалогу, независимо от используемого контракта.  
  
 Если аргумент CONTRACT_NAME не был указан, то свойство контракта приоритета диалога не изменяется.  
  
 LOCAL_SERVICE_NAME = {*LocalServiceName* | **ANY**}  
 Указывает имя службы, которая будет использоваться в качестве критерия для определения применимости приоритета к конечной точке диалога.  
  
 *LocalServiceName* — [!INCLUDE[ssDE](../../includes/ssde-md.md)] идентификатор и необходимо указать имя службы в текущей базе данных.  
  
 *LocalServiceName*  
 Указывает, что объектом применения приоритета диалога может быть:  
  
-   Любая конечная точка диалога инициатора, имя вызывающей службы совпадает *LocalServiceName*.  
  
-   Любой целевой конечной точке диалога, имя целевой службы соответствует *LocalServiceName*.  
  
 ANY  
 -   Указывает, что приоритет может применяться к любой конечной точке диалога, независимо от имени локальной службы, используемой точкой.  
  
 Если аргумент LOCAL_SERVICE_NAME не был указан, то свойство локальной службы приоритета диалога не изменяется.  
  
 REMOTE_SERVICE_NAME = {'*RemoteServiceName*"| **ANY**}  
 Указывает имя службы, которая будет использоваться в качестве критерия для определения применимости приоритета к конечной точке диалога.  
  
 *RemoteServiceName* — это литерал типа **nvarchar(256)**. [!INCLUDE[ssSB](../../includes/sssb-md.md)]использует сравнение байт за байтом *RemoteServiceName* строка. При сравнении учитывается регистр и не применяются текущие параметры сортировки. Целевая служба может располагаться в текущем экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] или в удаленном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 '*RemoteServiceName*'  
 Задает приоритет диалога, который будет иметь:  
  
-   Любая конечная точка диалога инициатора, имя целевой службы соответствует *RemoteServiceName*.  
  
-   Любой целевой конечной точки диалога, имя которого вызывающей службы совпадает *RemoteServiceName*.  
  
 ANY  
 Указывает, что приоритет диалога будет применяться ко всем конечным точкам диалога, вне зависимости от имен удаленных служб, связанных с ними.  
  
 Если аргумент REMOTE_SERVICE_NAME не был указан, то свойство удаленной службы приоритета диалога не изменяется.  
  
 Параметра PRIORITY_LEVEL = { *PriorityValue* | **по умолчанию** }  
 Задает уровень приоритета, который будет присвоен любой конечной точке диалога, использующей контракты и службы, указанные в приоритете диалога. *PriorityValue* должно быть целым литералом в диапазоне от 1 (наименьший приоритет) до 10 (наибольший приоритет).  
  
 Если аргумент PRIORITY_LEVEL не был указан, то свойство уровня приоритета для приоритета диалога не изменяется.  
  
## <a name="remarks"></a>Remarks  
 Свойства, измененные с помощью инструкции ALTER BROKER PRIORITY, не применяются к существующим диалогам. Существующие диалоги будут использовать приоритет, который был задан при их запуске.  
  
 Дополнительные сведения см. в разделе [CREATE BROKER PRIORITY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-broker-priority-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Разрешение на создание приоритета диалога по умолчанию имеют члены **db_ddladmin** или **db_owner** предопределенных ролей базы данных, а в **sysadmin** предопределенной роли сервера. Необходимо разрешение ALTER на базу данных.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-changing-only-the-priority-level-of-an-existing-conversation-priority"></a>A. Изменение только уровня приоритета существующего диалога.  
 Изменяет уровень приоритета, но не изменяет свойства контракта, локальной службы и удаленной службы.  
  
```  
ALTER BROKER PRIORITY SimpleContractDefaultPriority  
    FOR CONVERSATION  
    SET (PRIORITY_LEVEL = 3);  
```  
  
### <a name="b-changing-all-of-the-properties-of-an-existing-conversation-priority"></a>Б. Изменение всех свойств приоритета существующего диалога.  
 Изменяет свойства уровня приоритета, контракта, локальной и удаленной служб.  
  
```  
ALTER BROKER PRIORITY SimpleContractPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContractB,  
         LOCAL_SERVICE_NAME = TargetServiceB,  
         REMOTE_SERVICE_NAME = N'InitiatorServiceB',  
         PRIORITY_LEVEL = 8);  
```  
  
## <a name="see-also"></a>См. также  
 [СОЗДАТЬ ПРИОРИТЕТ БРОКЕРА &#40; Transact-SQL &#41;](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [DROP BROKER PRIORITY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [sys.conversation_priorities &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  
