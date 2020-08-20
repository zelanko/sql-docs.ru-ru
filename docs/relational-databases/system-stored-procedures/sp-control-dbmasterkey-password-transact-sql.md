---
description: sp_control_dbmasterkey_password (Transact-SQL)
title: sp_control_dbmasterkey_password (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/09/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_control_dbmasterkey_password
- sp_control_dbmasterkey_password_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_control_dbmasterkey_password
ms.assetid: 63979a87-42a2-446e-8e43-30481faaf3ca
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 08b749ad756a47ed991acd1ad0ea1d533bbb770c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481460"
---
# <a name="sp_control_dbmasterkey_password-transact-sql"></a>sp_control_dbmasterkey_password (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Добавляет или удаляет учетные данные, содержащие пароль, необходимый для открытия главного ключа базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_control_dbmasterkey_password @db_name = 'database_name,  
     @password = 'master_key_password' , @action = { 'add' | 'drop' }  
```  
  
## <a name="arguments"></a>Аргументы  
 @db_name= N '*database_name*'  
 Указывает имя базы данных, ассоциированной с этими учетными данными. База данных не может быть системной. *database_name* имеет тип **nvarchar**.  
  
 @password= N '*Password*'  
 Указывает пароль для главного ключа. *Password* имеет тип **nvarchar**.  
  
 @action= Н'адд '  
 Указывает на то, что учетные данные для указанной базы данных будет добавлены в хранилище учетных данных. Учетные данные будут содержать пароль главного ключа базы данных. Значение, передаваемое в @action , имеет тип **nvarchar**.  
  
 @action= Н'дроп '  
 Указывает на то, что учетные данные для указанной базы данных будет удалены из хранилища учетных данных. Значение, передаваемое в @action , имеет тип **nvarchar**.  
  
## <a name="remarks"></a>Комментарии  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нужен главный ключ базы данных для расшифровки или шифрования ключа, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается расшифровать главный ключ базы данных с помощью главного ключа службы экземпляра. Если расшифровка заканчивается неудачей, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет в хранилище учетных данных поиск учетных данных главного ключа, имеющих идентификатор GUID того же семейства, что и у базы данных, для которой нужен главный ключ. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается расшифровать главный ключ базы данных с помощью всех подходящих учетных данных, пока не удастся расшифровать ключ или пока не кончатся учетные данные.  
  
> [!CAUTION]  
>  Не создавайте учетные данные главного ключа для базы данных, которая должна быть недоступна sa и другим привилегированным участникам [системы безопасности] на уровне сервера. База данных может быть настроена таким образом, чтобы иерархия ее ключей не могла быть расшифрована главным ключом службы. Этот параметр поддерживается для максимальной защиты баз данных, содержащих зашифрованные сведения, которые не должны быть доступны sa или другим привилегированным участникам [системы безопасности] на уровне сервера. Создание учетных данных главного ключа для такой базы данных сводит на нет эту защиту, позволяя sa и другим привилегированным участникам [системы безопасности] на уровне сервера расшифровывать базу данных.  
  
 Учетные данные, созданные с помощью sp_control_dbmasterkey_password, отображаются в представлении каталога [sys. master_key_passwords](../../relational-databases/system-catalog-views/sys-master-key-passwords-transact-sql.md) . Имена учетных данных, создаваемых для главных ключей базы данных, имеют следующий формат: `##DBMKEY_<database_family_guid>_<random_password_guid>##` . Пароль хранится как секретные учетные данные. Для каждого пароля, добавленного в хранилище учетных данных, существует строка в представлении sys.credentials.  
  
 Нельзя использовать sp_control_dbmasterkey_password для создания учетных данных для следующих системных баз данных: Master, Model, msdb или tempdb.  
  
 Процедура sp_control_dbmasterkey_password не проверяет возможность пароля открывать главный ключ указанной базы данных.  
  
 Если задан пароль, который уже хранится в учетных данных для указанной базы данных, выполнение процедуры sp_control_dbmasterkey_password будет завершено неудачно.  
  
> [!NOTE]  
>  Две базы данных из различных экземпляров сервера могут иметь один и тот же идентификатор GUID семейства. Если такое происходит, базы данных будут иметь одну и ту же запись главного ключа в хранилище учетных данных.  
  
 Параметры, переданные в процедуру sp_control_dbmasterkey_password, не появляются в трассировках.  
  
> [!NOTE]  
>  Если учетные данные, добавленные с помощью процедуры sp_control_dbmasterkey_password, используются для открытия главного ключа базы данных, то главный ключ базы данных повторно шифруется главным ключом службы. Если база данных находится в режиме только для чтения, то операция повторного шифрования оканчивается неудачей и главный ключ базы данных останется незашифрованным. Для последующего доступа к главному ключу базы данных необходимо использовать инструкцию OPEN MASTER KEY и пароль. Чтобы избежать необходимости использовать пароль, создавайте учетные данные до того, как база данных будет переведена в режим только для чтения.  
  
 **Потенциальная ошибка обратной совместимости:** В настоящее время хранимая процедура не проверяет, существует ли главный ключ. Это разрешено для обратной совместимости, но при этом отображается предупреждение. Такое поведение является устаревшим. В следующем выпуске должен существовать главный ключ, а пароль, используемый в хранимой процедуре **sp_control_dbmasterkey_password** , должен совпадать с одним из паролей, используемых для шифрования главного ключа базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-credential-for-the-adventureworks2012-master-key"></a>A. Создание учетных данных для главного ключа AdventureWorks2012  
 В следующем примере создаются учетные данные для главного ключа базы данных `AdventureWorks2012`, пароль главного ключа сохраняется в виде секретного кода в учетных данных. Поскольку все параметры, передаваемые в, `sp_control_dbmasterkey_password` должны иметь тип данных **nvarchar**, текстовые строки преобразуются с помощью оператора приведения `N` .  
  
```  
EXEC sp_control_dbmasterkey_password @db_name = N'AdventureWorks2012',   
    @password = N'sdfjlkj#mM00sdfdsf98093258jJlfdk4', @action = N'add';  
GO  
```  
  
### <a name="b-dropping-a-credential-for-a-database-master-key"></a>Б. Удаление учетных данных для главного ключа базы данных  
 В следующем примере удаляются учетные данные, созданные в примере A. Обратите внимание, что все параметры являются обязательными, включая пароль.  
  
```  
EXEC sp_control_dbmasterkey_password @db_name = N'AdventureWorks2012',   
    @password = N'sdfjlkj#mM00sdfdsf98093258jJlfdk4', @action = N'drop';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка зашифрованной зеркальной базы данных](../../database-engine/database-mirroring/set-up-an-encrypted-mirror-database.md)   
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Учетные данные (компонент Database Engine)](../../relational-databases/security/authentication-access/credentials-database-engine.md)  
  
  
