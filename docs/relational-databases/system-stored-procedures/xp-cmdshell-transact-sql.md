---
title: xp_cmdshell (Трансакт-СЗЛ) Документы Майкрософт
ms.custom: ''
ms.date: 03/30/2020
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
ms.openlocfilehash: 2ce32fc31373077418e77d31ce064d60e23f1b24
ms.sourcegitcommit: fc5b757bb27048a71bb39755648d5cefe25a8bc6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80402693"
---
# <a name="xp_cmdshell-transact-sql"></a>xp_cmdshell (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Увеличивает число процессов командного ядра Windows в строке для выполнения. Любые выходные данные возвращаются в виде текстовых строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_cmdshell { 'command_string' } [ , no_output ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **'** *command_string'* **'**  
 Строка, содержащая команду для передачи операционной системе. *command_string* **varchar (8000)** или **nvarchar (4000)**, без по умолчанию. *command_string* не может содержать более одного набора двойных кавычек. Требуется одна пара кавычек, если какие-либо пробелы присутствуют в пути файла или названия программы, на которые ссылаются *в command_string.* Если входящие пробелы вызывают неполадки, то следует присваивать файлам имена в формате FAT 8.3.  
  
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
  
 Строки возвращаются в **nvarchar (255)** столбец. Если используется **no_output** опция, будет возвращено только следующее:  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>Remarks  
 Процесс Windows, порожденный **xp_cmdshell,** имеет те [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] же права безопасности, что и учетная запись службы.  
  
 **xp_cmdshell** работает синхронно. Управление не возвращается участнику до завершения команды ядра.  
  
 **xp_cmdshell** может быть включен и отключен с помощью управления на основе политики или выполнения **sp_configure.** Для получения дополнительной информации [см. конфигурацию поверхности и](../../relational-databases/security/surface-area-configuration.md) [xp_cmdshell вариант конфигурации сервера.](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)  
  
> [!IMPORTANT]
>  Если **xp_cmdshell** выполняется в пакете и возвращает ошибку, пакет выйдет из строя.
  
## <a name="xp_cmdshell-proxy-account"></a>Учетная запись-посредник для процедуры xp_cmdshell  
 Когда он вызывается пользователем, который не является членом **сисадмин** фиксированной роли сервера, **xp_cmdshell** подключается к Windows, используя имя учетной записи и пароль, хранящийся в учетных данных под названием **"#xp_cmdshell_proxy_account "** Если этого прокси-верификатора не существует, **xp_cmdshell** потерпит неудачу.  
  
 Учетные данные учетной записи прокси могут быть созданы путем выполнения **sp_xp_cmdshell_proxy_account.** В качестве аргумента эта хранимая процедура обрабатывает имя пользователя Windows и пароль. Например, следующая команда создает посреднические учетные записи-посредники для пользователя домена Windows `SHIPPING\KobeR` с паролем Windows `sdfh%dkc93vcMt0`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 Для получения дополнительной информации [&#41;&#40;sp_xp_cmdshell_proxy_account ](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)см.  
  
## <a name="permissions"></a>Разрешения  
 Поскольку вредоносные пользователи иногда пытаются повысить свои привилегии, используя **xp_cmdshell,** **xp_cmdshell** отключен по умолчанию. Для этого используйте **управление sp_configure** или **политикой.** Дополнительные сведения см. в разделе [Параметр конфигурации сервера xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 При первом включении **xp_cmdshell** требуется разрешение CONTROL SERVER для выполнения, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] процесс Windows, созданный **xp_cmdshell,** имеет тот же контекст безопасности, что и учетная запись службы. Учетная [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запись службы часто имеет больше разрешений, чем необходимо для работы, выполняемой процессом, созданным **xp_cmdshell.** Для повышения безопасности доступ к **xp_cmdshell** должен быть ограничен для привилегированных пользователей.  
  
 Чтобы позволить неадминистраторам использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **xp_cmdshell**и создавать процессы создания детских процессов с маркером безопасности менее привилегировой учетной записи, выполните следующие действия:  
  
1.  Создайте и настройте локальную учетную запись Windows или учетную запись домена с меньшими правами доступа, чем требуется процессу.  
  
2.  Используйте процедуру **системы sp_xp_cmdshell_proxy_account** для настройки **xp_cmdshell** для использования этой наименее привилегировой учетной записи.  
  
    > [!NOTE]  
    >  Вы также можете настроить эту [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] учетную запись прокси, используя право нажав **Свойства** на имя сервера в Object Explorer, и глядя на вкладку **безопасности** для раздела **прокси-аккаунта Сервера.**  
  
3.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], используя мастер-базу `GRANT exec ON xp_cmdshell TO N'<some_user>';` данных, выполнить заявление, чтобы дать конкретным пользователям, не**сисадмин** возможность выполнения **xp_cmdshell.** Указанный пользователь должен существовать в основной базе данных.  
  
 Теперь неадминистраторы могут запускать процессы операционной системы с **xp_cmdshell** и эти процессы запускались с разрешения настроенной учетной записью прокси. Пользователи с разрешением CONTROL SERVER (члены фиксированной роли **сервера sysadmin)** будут продолжать получать разрешения учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы для детских процессов, запущенных **xp_cmdshell.**  
  
 Чтобы определить учетную запись Windows, используемую **xp_cmdshell** при запуске операционных процессов системы, выполните следующее заявление:  
  
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
 В следующем примере `xp_cmdshell` расширенная процедура хранения также предполагает статус возвращения. Значение кода возврата хранится в переменной `@result`.  
  
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
 [Общие расширенные процедуры хранения &#40;&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_cmdshell вариант конфигурации сервера](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [Конфигурация поверхностной зоны](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account&#41;&#40;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  
