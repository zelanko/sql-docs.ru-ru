---
description: ALTER SERVICE MASTER KEY (Transact-SQL)
title: ALTER SERVICE MASTER KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_SERVICE_MASTER_KEY_TSQL
- ALTER SERVICE MASTER KEY
dev_langs:
- TSQL
helpviewer_keywords:
- REGENERATE phrase
- FORCE option
- ALTER SERVICE MASTER KEY statement
- cryptography [SQL Server], Service Master Key
- modifying Service Master Key
- decryption [SQL Server], Service Master Key
- encryption [SQL Server], Service Master Key
- service master key [SQL Server], modifying
ms.assetid: a1e9be0e-4115-47d8-9d3a-3316d876a35e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 53526aa2ba6a59b623382aa1c47b11443759756b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88426826"
---
# <a name="alter-service-master-key-transact-sql"></a>ALTER SERVICE MASTER KEY (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Изменяет главный ключ службы экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
ALTER SERVICE MASTER KEY   
    [ { <regenerate_option> | <recover_option> } ] [;]  
  
<regenerate_option> ::=  
    [ FORCE ] REGENERATE  
  
<recover_option> ::=  
    { WITH OLD_ACCOUNT = 'account_name' , OLD_PASSWORD = 'password' }  
    |      
    { WITH NEW_ACCOUNT = 'account_name' , NEW_PASSWORD = 'password' }  
```  
  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 FORCE  
 Указывает, что главный ключ службы должен быть принудительно создан повторно, даже если это может привести к потере данных. Дополнительные сведения см. в разделе [Изменение учетной записи службы SQL Server](#_changing) далее в этой теме.  
  
 REGENERATE  
 Указывает, что главный ключ службы должен быть создан повторно.  
  
 OLD_ACCOUNT **='***account_name***'**  
 Указывает имя старой учетной записи службы Windows.  
  
> [!WARNING]  
>  Данный параметр является устаревшим. Не используется. Взамен используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 OLD_PASSWORD **='***password***'**  
 Указывает пароль старой учетной записи службы Windows.  
  
> [!WARNING]  
>  Данный параметр является устаревшим. Не используется. Взамен используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 NEW_ACCOUNT **='***account_name***'**  
 Указывает имя новой учетной записи службы Windows.  
  
> [!WARNING]  
>  Данный параметр является устаревшим. Не используется. Взамен используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 NEW_PASSWORD **='***password***'**  
 Указывает пароль новой учетной записи службы Windows.  
  
> [!WARNING]  
>  Данный параметр является устаревшим. Не используется. Взамен используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Remarks  
 Главный ключ службы автоматически создается в первый раз, когда он требуется для шифрования пароля связанного сервера, учетных данных или главного ключа базы данных. Главный ключ службы шифруется с помощью ключа локального компьютера или интерфейса API защиты данных Windows. Этот API использует ключ, получаемый из учетных данных Windows, которые соответствуют учетной записи службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] использует для защиты главного ключа службы и главного ключа базы данных алгоритм шифрования AES. AES - это новый алгоритм шифрования, отличный от алгоритма 3DES, используемого в более ранних версиях. После обновления экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] необходимо заново сформировать главный ключ службы и главный ключ базы данных, чтобы обновить главные ключи до алгоритма AES. Дополнительные сведения о повторном создании главного ключа базы данных см. в статье [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md).  
  
##  <a name="changing-the-sql-server-service-account"></a><a name="_changing"></a> Изменение учетной записи службы SQL Server  
 Чтобы изменить учетную запись службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для управления учетной записью службы и изменения записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит дополнительную копию главного ключа службы, защищенную учетной записью компьютера, которая обладает необходимыми разрешениями, предоставляемыми группе служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если выполняется перестроение компьютера, то главный ключ службы может быть восстановлен тем же пользователем домена, который раньше использовался учетной записью службы. Такой метод не работает с локальными учетными записями, а также с учетными записями Local System, Local Service и Network Service. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перемещается на другой компьютер, выполните миграцию главного ключа службы с помощью резервного копирования и восстановления.  
  
 Фраза REGENERATE повторно создает главный ключ службы. При повторном создании главного ключа службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расшифровывает все ключи, которые были зашифрованы главным ключом, а затем шифрует их новым главным ключом службы. Эта операция требовательна к вычислительным ресурсам. Рекомендуется назначать ее выполнение на периоды низкой загрузки системы, кроме случаев получения несанкционированного доступа к ключу. В случае ошибки любой из операций дешифрования выполнение инструкции в целом также завершается ошибкой.  
  
 Установка параметра FORCE вызывает продолжение процесса повторного создания ключа даже в том случае, когда не удается получить текущий главный ключ или расшифровать все зашифрованные им закрытые ключи. Используйте параметр FORCE, только если повторное создание ключа заканчивается неудачей, и невозможно восстановить главный ключ службы с помощью инструкции [RESTORE SERVICE MASTER KEY](../../t-sql/statements/restore-service-master-key-transact-sql.md).  
  
> [!CAUTION]  
>  Главный ключ службы является корнем иерархии шифрования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Главный ключ службы прямо или непрямо защищает все другие ключи и секретные данные в иерархии шифрования. Если зависящий от него ключ не удастся расшифровать во время принудительного повторного создания главного ключа, то защищаемые этим ключом данные будут потеряны.  
  
 При перемещении SQL на другой компьютер следует использовать одну и ту же учетную запись службы для дешифрования главного ключа службы — SQL Server фиксирует шифрование учетной записи компьютера автоматически.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER на сервер.  
  
## <a name="examples"></a>Примеры  
 Следующий пример иллюстрирует повторное создание главного ключа службы.  
  
```  
ALTER SERVICE MASTER KEY REGENERATE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [RESTORE SERVICE MASTER KEY (Transact-SQL)](../../t-sql/statements/restore-service-master-key-transact-sql.md)   
 [BACKUP SERVICE MASTER KEY (Transact-SQL)](../../t-sql/statements/backup-service-master-key-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
