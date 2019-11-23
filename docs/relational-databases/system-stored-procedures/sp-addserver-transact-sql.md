---
title: sp_addserver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addserver
- sp_addserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addserver
- renaming servers
- machine names [SQL Server]
- computer names
ms.assetid: 160a6b29-5e80-44ab-80ec-77d4280f627c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8924a2a5c0960137eb5fe2a78d2ea7f3521b3929
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381720"
---
# <a name="sp_addserver-transact-sql"></a>sp_addserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет имя локального экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При переименовании компьютера, на котором размещается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте **sp_addserver** , чтобы сообщить экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] нового имени компьютера. Эта процедура должна быть выполнена на всех экземплярах компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , размещенных на компьютере. Невозможно изменить имя компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Чтобы изменить имя экземпляра, установите новый экземпляр с нужным именем, отключите файлы базы данных от старого экземпляра, подключите базы данных к новому экземпляру и удалите старый экземпляр. Кроме того, вы можете создать имя псевдонима клиента на клиентском компьютере, перенаправив подключение на другой сервер, и имя экземпляра или комбинацию **сервер:порт** , не изменяя имя экземпляра на сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addserver [ @server = ] 'server' ,  
     [ @local = ] 'local'   
     [ , [ @duplicate_ok = ] 'duplicate_OK' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @server = ] 'server'` — имя сервера. Имена серверов должны быть уникальными и соответствовать правилам именования [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, за исключением того, что пробелы не допускаются. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 Если на одном компьютере установлено несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то каждый экземпляр работает, как на отдельном сервере. Укажите именованный экземпляр, обратившись к *серверу* как *servername\instancename*.  
  
`[ @local = ] 'LOCAL'` указывает, что сервер добавляется в качестве локального сервера. **\@Local** имеет тип **varchar (10)** и значение по умолчанию NULL. При указании **\@Local** в качестве **локального** определяется **\@Server** в качестве имени локального сервера и вызывается функция @@SERVERNAME для возврата значения *Server*.  
  
 Программа настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время установки присваивает этой переменной в качестве значения имя компьютера. По умолчанию при подключении пользователей к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется имя компьютера, и никакая дополнительная настройка не требуется.  
  
 Локальное переопределение вступает в силу только после перезагрузки компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . На каждом экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]может быть определен только один локальный сервер.  
  
`[ @duplicate_ok = ] 'duplicate_OK'` указывает, разрешено ли повторяющееся имя сервера. **\@duplicate_OK** имеет тип **varchar (13)** и значение по умолчанию NULL. **\@duplicate_OK** может иметь только значение **duplicate_OK** или null. Если указано **duplicate_OK** и добавляемое имя сервера уже существует, ошибка не возникает. Если именованные параметры не используются, необходимо указать **\@Local** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 Чтобы задать или очистить параметры сервера, используйте **sp_serveroption**.  
  
 **sp_addserver** нельзя использовать внутри определяемой пользователем транзакции.  
  
 Использование **sp_addserver** для добавления удаленного сервера прекращено. Вместо этого используйте хранимую процедуру [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера **setupadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере запись компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , содержащая имя компьютера, на котором размещается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , изменяется на `ACCOUNTS`.  
  
```  
sp_addserver 'ACCOUNTS', 'local';  
```  
  
## <a name="see-also"></a>См. также статью  
 [Переименование компьютера, на котором размещен изолированный экземпляр SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropserver &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)  
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
