---
title: xp_cmdshell (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 12/01/2019
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
ms.openlocfilehash: 2ffe3197f74e274792ee1a3f97d700492a018bef
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85633753"
---
# <a name="xp_cmdshell-transact-sql"></a>xp_cmdshell (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Увеличивает число процессов командного ядра Windows в строке для выполнения. Любые выходные данные возвращаются в виде текстовых строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_cmdshell { 'command_string' } [ , no_output ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *command_string* **"**  
 Строка, содержащая команду для передачи операционной системе. *command_string* имеет тип **varchar (8000)** или **nvarchar (4000)** и не имеет значения по умолчанию. *command_string* не может содержать более одного набора двойных кавычек. При наличии пробелов в путях к файлам или именах программ, на которые имеются ссылки в *command_string*, требуется одиночная пара кавычек. Если входящие пробелы вызывают неполадки, то следует присваивать файлам имена в формате FAT 8.3.  
  
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
  
 Строки возвращаются в столбце **nvarchar (255)** . Если используется параметр **no_output** , будут возвращены только следующие из них:  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>Примечания  
 Процесс Windows, порожденный **xp_cmdshell** , имеет те же права безопасности, что и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы.  
  
 **xp_cmdshell** работает синхронно. Управление не возвращается участнику до завершения команды ядра.  
  
 **xp_cmdshell** можно включить и отключить, используя управление на основе политик или выполнив **sp_configure**. Дополнительные сведения см. в разделе Конфигурация [контактной зоны](../../relational-databases/security/surface-area-configuration.md) и [параметр конфигурации сервера xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
> [!IMPORTANT]
>  Если **xp_cmdshell** выполняется в пакете и возвращает ошибку, пакет завершится ошибкой. Это изменение поведения. В более ранних версиях [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пакета будет продолжать выполняться.  
  
## <a name="xp_cmdshell-proxy-account"></a>Учетная запись-посредник для процедуры xp_cmdshell  
 При вызове пользователем, который не является членом предопределенной роли сервера **sysadmin** , **xp_cmdshell** подключается к Windows, используя имя учетной записи и пароль, хранящиеся в учетных данных с именем **# #xp_cmdshell_proxy_account # #**. Если учетные данные прокси-сервера не существуют, **xp_cmdshell** завершится ошибкой.  
  
 Учетные данные учетной записи-посредника можно создать, выполнив **sp_xp_cmdshell_proxy_account**. В качестве аргумента эта хранимая процедура обрабатывает имя пользователя Windows и пароль. Например, следующая команда создает посреднические учетные записи-посредники для пользователя домена Windows `SHIPPING\KobeR` с паролем Windows `sdfh%dkc93vcMt0`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 Дополнительные сведения см. в разделе [sp_xp_cmdshell_proxy_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Так как злоумышленники иногда пытаются повысить свои привилегии с помощью **xp_cmdshell**, **xp_cmdshell** по умолчанию отключена. Используйте **sp_configure** или **Управление на основе политик** , чтобы включить ее. Дополнительные сведения см. в разделе [Параметр конфигурации сервера xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 При первом включении **xp_cmdshell** требуется разрешение CONTROL Server для выполнения, а процесс Windows, созданный **xp_cmdshell** , имеет тот же контекст безопасности, что и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Учетная запись службы часто имеет больше разрешений, чем требуется для работы, выполняемой процессом, созданным **xp_cmdshell**. Для повышения безопасности доступ к **xp_cmdshell** должен быть ограничен пользователями с высоким уровнем привилегий.  
  
 Чтобы разрешить Неадминистраторам использовать **xp_cmdshell**и разрешить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создавать дочерние процессы с маркером безопасности учетной записи с меньшими привилегиями, выполните следующие действия.  
  
1.  Создайте и настройте локальную учетную запись Windows или учетную запись домена с меньшими правами доступа, чем требуется процессу.  
  
2.  Используйте **sp_xp_cmdshell_proxy_account** системную процедуру, чтобы настроить **xp_cmdshell** для использования учетной записи с минимальными правами доступа.  
  
    > [!NOTE]  
    >  Можно также настроить эту учетную запись-посредник [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , щелкнув правой кнопкой мыши **свойства** имени сервера в обозревателе объектов и перейдя на вкладку **Безопасность** раздела **учетная запись-посредник сервера** .  
  
3.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] с помощью базы данных master выполните `GRANT exec ON xp_cmdshell TO N'<some_user>';` инструкцию, чтобы предоставить отдельным пользователям, не являющимся системными**администраторами** , возможность выполнять **xp_cmdshell**. Указанный пользователь должен существовать в базе данных master.  
  
 Теперь пользователи, не являющиеся администраторами, могут запускать процессы операционной системы с **xp_cmdshell** , а эти процессы выполняются с разрешениями настроенной учетной записи-посредника. Пользователи с разрешением CONTROL SERVER (члены предопределенной роли сервера **sysadmin** ) будут по-прежнему принимать разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы для дочерних процессов, запускаемых **xp_cmdshell**.  
  
 Чтобы определить учетную запись Windows, используемую **xp_cmdshell** при запуске процессов операционной системы, выполните следующую инструкцию:  
  
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
EXEC master..xp_cmdshell 'dir *.exe'  
```  
  
### <a name="b-returning-no-output"></a>Б. Применение без возврата данных  
 В следующем примере процедура `xp_cmdshell` применяется для выполнения командной строки без возвращения данных клиенту.  
  
```  
USE master;  
  
EXEC xp_cmdshell 'copy c:\SQLbcks\AdvWorks.bck  
    \\server2\backups\SQLbcks', NO_OUTPUT;  
GO  
```  
  
### <a name="c-using-return-status"></a>В. Применение возвращаемого состояния  
 В следующем примере `xp_cmdshell` Расширенная хранимая процедура также предлагает состояние возврата. Значение кода возврата хранится в переменной `@result`.  
  
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
 [Параметр конфигурации сервера xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [Настройка контактной зоны](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  
