---
title: sp_addserver (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 08224c1f35e0115ba3bb97f88b0a2a51f5e05a6a
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="spaddserver-transact-sql"></a>sp_addserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет имя локального экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если компьютер, где размещена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является переименован, используйте **sp_addserver** для информирования экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] нового имени компьютера. Эта процедура должна быть выполнена на всех экземплярах компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], размещенных на компьютере. Имя экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)] не может быть изменено. Чтобы изменить имя экземпляра, установите новый экземпляр с нужным именем, отключите файлы базы данных от старого экземпляра, подключите базы данных к новому экземпляру и удалите старый экземпляр. Кроме того, вы можете создать имя псевдонима клиента на клиентском компьютере, перенаправив подключение на другой сервер, и имя экземпляра или комбинацию **сервер:порт** , не изменяя имя экземпляра на сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addserver [ @server = ] 'server' ,  
     [ @local = ] 'local'   
     [ , [ @duplicate_ok = ] 'duplicate_OK' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@server =** ] **'***server***'**  
 Имя сервера. Имена серверов должны быть уникальными и соответствовать правилам именования [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, за исключением того, что пробелы не допускаются. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 Если несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливаются на компьютере, каждый экземпляр работает, как если бы он находится на отдельном сервере. Укажите именованный экземпляр, обратившись к *сервера* как *имя_сервера\имя_экземпляра*.  
  
 [  **@local =** ] **'LOCAL'**  
 Указывает, что добавляемый сервер — локальный. **@local** — **varchar(10)**, значение по умолчанию NULL. Указание **@local** как **ЛОКАЛЬНОГО** определяет **@server** как имя локального сервера и причины @@SERVERNAME функция, возвращающая значение из *сервера*.  
  
 Программа настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время установки присваивает этой переменной в качестве значения имя компьютера. По умолчанию имя компьютера является подключении пользователей к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] без дополнительной настройки.  
  
 Локальное переопределение вступает в силу только после перезагрузки компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. На каждом экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] может быть определен только один локальный сервер.  
  
 [  **@duplicate_ok =** ] **«duplicate_OK»**  
 Указывает, допустимо ли совпадение имен серверов. **@duplicate_OK** — **varchar(13)**, значение по умолчанию NULL. **@duplicate_OK** может иметь только значение **duplicate_OK** или иметь значение NULL. Если **duplicate_OK** указан и имя сервера, который добавляется уже существует, ошибка не возникает. Если именованные параметры не используются, **@local** должен быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Чтобы задать или Очистить параметры сервера, используйте **sp_serveroption**.  
  
 **sp_addserver** нельзя использовать внутри пользовательской транзакции.  
  
 С помощью **sp_addserver** для добавления удаленного сервера более не поддерживается. Вместо этого используйте хранимую процедуру [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера **setupadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере изменяется [!INCLUDE[ssDE](../../includes/ssde-md.md)] запись для имени компьютера, на котором размещается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для `ACCOUNTS`.  
  
```  
sp_addserver 'ACCOUNTS', 'local';  
```  
  
## <a name="see-also"></a>См. также  
 [Переименование компьютера, на который установлен изолированный экземпляр SQL Server](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_helpserver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
