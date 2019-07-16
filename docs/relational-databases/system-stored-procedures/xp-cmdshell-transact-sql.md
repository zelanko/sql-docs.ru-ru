---
title: xp_cmdshell (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_cmdshell
- xp_cmdshell_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: 18935cf4-b320-4954-b6c1-e007fcefe358
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b01628e339e4a3ce1f824f27edd75e2e5aea2526
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68123773"
---
# <a name="xpcmdshell-transact-sql"></a>xp_cmdshell (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Увеличивает число процессов командного ядра Windows в строке для выполнения. Любые выходные данные возвращаются в виде текстовых строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_cmdshell { 'command_string' } [ , no_output ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *command_string* **"**  
 Строка, содержащая команду для передачи операционной системе. *command_string* — **varchar(8000)** или **nvarchar(4000)** , не имеет значения по умолчанию. *command_string* не может содержать более одного набора двойных кавычек. Одной пары кавычек является обязательным, если все пробелы в пути к файлам или именах программ в аргументе *command_string*. Если входящие пробелы вызывают неполадки, то следует присваивать файлам имена в формате FAT 8.3.  
  
 **no_output**  
 Необязательный параметр, указывающий, что клиенту не следует возвращать выходные данные.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Выполнение следующей процедуры `xp_cmdshell` возвращает листинг текущего каталога.  
  
```  
EXEC xp_cmdshell 'dir *.exe';  
GO  
```  
  
 Строки возвращаются в **nvarchar(255)** столбца. Если **no_output** используется параметр, будут возвращены только следующие:  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>Примечания  
 Процесс Windows, сформированными **xp_cmdshell** имеет те же права, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы.  
  
 **xp_cmdshell** работает синхронно. Управление не возвращается участнику до завершения команды ядра.  
  
 **xp_cmdshell** можно включать и отключать с помощью управления на основе политик или путем выполнения **sp_configure**. Дополнительные сведения см. в разделе [настройки контактной зоны](../../relational-databases/security/surface-area-configuration.md) и [параметр конфигурации сервера xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
> [!IMPORTANT]
>  Если **xp_cmdshell** выполняется в пакете и возвращает сообщение об ошибке пакета завершится ошибкой. Это изменение поведения. В более ранних версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пакета продолжилось бы для выполнения.  
  
## <a name="xpcmdshell-proxy-account"></a>Учетная запись-посредник для процедуры xp_cmdshell  
 Если он вызывается пользователем, который не является членом **sysadmin** предопределенной роли сервера, **xp_cmdshell** подключается к Windows, используя имя учетной записи и пароль хранятся в учетных данных с именем **## #xp_cmdshell_proxy_account ##** . Если эти посреднические учетные данные не существует, **xp_cmdshell** завершится ошибкой.  
  
 Учетные данные учетной записи прокси-сервера можно создать, выполнив **sp_xp_cmdshell_proxy_account**. В качестве аргумента эта хранимая процедура обрабатывает имя пользователя Windows и пароль. Например, следующая команда создает посреднические учетные записи-посредники для пользователя домена Windows `SHIPPING\KobeR` с паролем Windows `sdfh%dkc93vcMt0`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 Дополнительные сведения см. в разделе [sp_xp_cmdshell_proxy_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Поскольку иногда пользователи-злоумышленники пытаются повысить свои полномочия с помощью **xp_cmdshell**, **xp_cmdshell** отключен по умолчанию. Используйте **sp_configure** или **управления на основе политик** Чтобы включить его. Дополнительные сведения см. в разделе [Параметр конфигурации сервера xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 При первом включении **xp_cmdshell** требуется разрешение CONTROL SERVER для выполнения и процесс Windows, созданных **xp_cmdshell** имеет тот же контекст безопасности, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Учетной записи службы часто имеет больше разрешений, чем это необходимо для работы, выполняемой процессом, созданные **xp_cmdshell**. В целях повышения безопасности доступа к **xp_cmdshell** должны быть только пользователи с высоким уровнем привилегий.  
  
 Чтобы разрешить пользователям без прав администратора использовать **xp_cmdshell**и разрешить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создавать дочерние процессы с маркером безопасности, менее привилегированной учетной записи, выполните следующие действия:  
  
1.  Создайте и настройте локальную учетную запись Windows или учетную запись домена с меньшими правами доступа, чем требуется процессу.  
  
2.  Используйте **sp_xp_cmdshell_proxy_account** системной процедуры для настройки **xp_cmdshell** использовать эту учетную запись с минимальными правами доступа.  
  
    > [!NOTE]  
    >  Можно также настроить этот прокси-сервер использует учетную запись [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] щелкните правой кнопкой мыши **свойства** на сервере, имя в обозревателе объектов и посмотрев **безопасности** вкладке **сервера Учетная запись-посредник** раздел.  
  
3.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], с помощью базы данных master, выполните `GRANT exec ON xp_cmdshell TO '<somelogin>'` инструкцию, чтобы предоставить конкретным отличных**sysadmin** пользователям возможность выполнять **xp_cmdshell**. Указанное имя входа необходимо сопоставить с пользователем в базе данных master.  
  
 Теперь пользователям без прав администратора могут запускать процессы операционной системы с **xp_cmdshell** и эти процессы будут запускаться с правами учетной записи-посредника, который вы настроили. Пользователи с разрешением CONTROL SERVER (члены **sysadmin** предопределенной роли сервера) продолжит получать разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы для дочерних процессов, которые запускаются с **xp_cmdshell** .  
  
 Для определения учетной записи Windows, которая используется **xp_cmdshell** при запуске процессов операционной системы, выполните следующую инструкцию:  
  
```  
xp_cmdshell 'whoami.exe'  
  
```  
  
 Чтобы определить контекст безопасности для другого имени входа, выполните следующее:  
  
```  
EXECUTE AS LOGIN = '<other_login>' ;  
GO  
xp_cmdshell 'whoami.exe' ;  
REVERT ;  
  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-a-list-of-executable-files"></a>A. Возвращение списка исполняемых файлов  
 В следующем примере показано, как расширенная хранимая процедура `xp_cmdshell` выполняет команду каталога.  
  
```  
EXEC master..xp_cmdshell 'dir *.exe''  
```  
  
### <a name="b-returning-no-output"></a>Б. Применение без возврата данных  
 В следующем примере процедура `xp_cmdshell` применяется для выполнения командной строки без возвращения данных клиенту.  
  
```  
USE master;  
  
EXEC xp_cmdshell 'copy c:\SQLbcks\AdvWorks.bck  
    \\server2\backups\SQLbcks, NO_OUTPUT';  
GO  
```  
  
### <a name="c-using-return-status"></a>В. Применение возвращаемого состояния  
 В следующем примере `xp_cmdshell` расширенной хранимой процедуры также предлагает возвращаемое состояние. Значение кода возврата хранится в переменной `@result`.  
  
```  
DECLARE @result int;  
EXEC @result = xp_cmdshell 'dir *.exe';  
IF (@result = 0)  
   PRINT 'Success'  
ELSE  
   PRINT 'Failure';  
```  
  
### <a name="d-writing-variable-contents-to-a-file"></a>Г. Запись содержимого переменной в файл  
 В следующем примере содержимое переменной `@var` записывается в файл с именем `var_out.txt` в текущем каталоге сервера.  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'Hello world';  
SET @cmd = 'echo ' + @var + ' > var_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
### <a name="e-capturing-the-result-of-a-command-to-a-file"></a>Д. Ввод результата команды в файл  
 В следующем примере содержимое текущего каталога записывается в файл с именем `dir_out.txt` в текущем каталоге сервера.  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'dir/p';  
SET @cmd = @var + ' > dir_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
## <a name="see-also"></a>См. также  
 [Общие расширенные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [Параметр конфигурации сервера «xp_cmdshell»](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [Настройка контактной зоны](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  
