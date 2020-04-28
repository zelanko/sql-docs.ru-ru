---
title: sp_dropserver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropserver_TSQL
- sp_dropserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropserver
ms.assetid: 0fc83e35-0caa-49a3-a4b6-a1890d4f46ef
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 0155b154a1d63343c157bc2eca6e5cbd7c1b8968
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124825"
---
# <a name="sp_dropserver-transact-sql"></a>sp_dropserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Удаляет сервер из списка известных удаленных и связанных серверов на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
sp_dropserver [ @server = ] 'server'   
     [ , [ @droplogins = ] { 'droplogins' | NULL} ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *сервером*  
 Удаляемый сервер. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию. *сервер* должен существовать.  
  
 *droplogins*  
 Указывает, что связанные имена входа удаленного и связанного сервера для *сервера* также должны быть удалены, если указан **droplogins** . **`@droplogins`** имеет **тип char (10)** и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 При запуске **sp_dropserver** на сервере со связанными удаленными и связанными записями входа, или в качестве издателя репликации, возвращается сообщение об ошибке. Чтобы удалить все имена входа удаленных и связанных серверов для сервера при удалении сервера, используйте аргумент **droplogins** .  
  
 **sp_dropserver** не может выполняться внутри определяемой пользователем транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LINKED SERVER на сервере.  
  
## <a name="examples"></a>Примеры  
 Следующий пример удаляет расположенный удаленно сервер `ACCOUNTS` и все связанные имена входа из локального экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
sp_dropserver 'ACCOUNTS', 'droplogins';  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
