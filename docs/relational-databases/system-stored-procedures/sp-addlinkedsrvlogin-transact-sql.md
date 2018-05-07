---
title: sp_addlinkedsrvlogin (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addlinkedsrvlogin_TSQL
- sp_addlinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlinkedsrvlogin
ms.assetid: eb69f303-1adf-4602-b6ab-f62e028ed9f6
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ce75eed42db1d03848b5ba905ce972b829596870
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spaddlinkedsrvlogin-transact-sql"></a>sp_addlinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает или обновляет сопоставления имен входа в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с учетной записью на удаленном сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addlinkedsrvlogin [ @rmtsrvname = ] 'rmtsrvname'   
     [ , [ @useself = ] 'TRUE' | 'FALSE' | NULL ]   
     [ , [ @locallogin = ] 'locallogin' ]   
     [ , [ @rmtuser = ] 'rmtuser' ]   
     [ , [ @rmtpassword = ] 'rmtpassword' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @rmtsrvname **=** ] **"***серверу rmtsrvname***"**  
 Имя связанного сервера, к которому применяется сопоставление имен входа. *серверу rmtsrvname* — **sysname**, не имеет значения по умолчанию.  
  
 [ @useself **=** ] **"** TRUE **"** | 'FALSE' | «NULL»  
 Определяет, следует ли устанавливать соединение *серверу rmtsrvname* с олицетворением локального имени входа или явной отправки имени входа и пароля. Тип данных является **varchar (** 8 **)**, значение по умолчанию TRUE.  
  
 Значение TRUE указывает, что имена входа используются собственные учетные данные для подключения к *серверу rmtsrvname*, с *rmtuser* и *rmtpassword* аргументы, которые обрабатываются. Значение FALSE указывает, что *rmtuser* и *rmtpassword* аргументы используются для подключения к *серверу rmtsrvname* для указанного *locallogin* . Если *rmtuser* и *rmtpassword* также являются значение равно NULL, без имени входа или пароль будет использоваться для подключения к связанному серверу.  
  
 [ @locallogin **=** ] **"***locallogin***"**  
 Имя входа на локальный сервер. *locallogin* — **sysname**, значение по умолчанию NULL. Значение NULL указывает, что данная запись применяется ко всем локальным именам входа, которые подключаются к *серверу rmtsrvname*. Если значение не NULL, *locallogin* может быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или имени входа Windows. Имени входа Windows должен быть предоставлен либо прямой доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], либо доступ через членство в группе Windows, обладающей нужными правами доступа.  
  
 [ @rmtuser **=** ] **"***rmtuser***"**  
 Удаленное имя входа, используемые для подключения к *серверу rmtsrvname* при @useself имеет значение FALSE. Если удаленный сервер является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не использующим проверку подлинности Windows, *rmtuser* — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа. *rmtuser* — **sysname**, значение по умолчанию NULL.  
  
 [ @rmtpassword **=** ] **"***rmtpassword***"**  
 Пароль, связанный с *rmtuser*. *rmtpassword* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Когда пользователь входит на локальный сервер и выполняет распределенный запрос, который обращается к таблице на связанном сервере, то для открытия таблицы локальный сервер должен войти на связанный сервер под именем данного пользователя. Учетные данные входа, с помощью которых локальный сервер будет входить на связанный сервер, задаются с помощью хранимой процедуры sp_addlinkedsrvlogin.  
  
> [!NOTE]  
>  Чтобы создать наиболее эффективный план запроса при использовании таблицы на связанном сервере, обработчик запроса должен иметь статистику распределения данных со связанного сервера. Пользователи, имеющие ограниченные разрешения для работы со столбцами таблицы, могут не иметь возможности получить необходимую статистику и, как следствие, получат менее эффективный план запроса. Если связанный сервер является экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для получения всей доступной статистики пользователь должен быть владельцем таблицы или членом предопределенной роли сервера sysadmin, db_owner или предопределенной роли базы данных db_ddladmin на связанном сервере. SQL Server 2012 c пакетом обновления 1 (SP1) изменяет разрешения для получения статистики и позволяет пользователям, имеющим разрешение SELECT, получать доступ к имеющейся статистике c помощью команды DBCC SHOW_STATISTICS. Дополнительные сведения см в разделе разрешения [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).  
  
 Сопоставление по умолчанию всех имен входа на локальном сервере с удаленными именами входа на связанном сервере создается автоматически при выполнении процедуры sp_addlinkedserver. Сопоставление по умолчанию заключается в том, что при соединении со связанным сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует учетные данные пользователя локального имени входа. Это эквивалентно выполнению процедуры с @useself значение **true** для связанного сервера без указания локального имени пользователя. С помощью процедуры sp_addlinkedsrvlogin следует только изменять сопоставления по умолчанию или добавлять новые сопоставления для определенных локальных имен входа. Сопоставление по умолчанию или любое другое сопоставление удаляется с помощью процедуры sp_droplinkedsrvlogin.  
  
 Вместо того чтобы создавать предопределенные сопоставления входных имен с помощью процедуры sp_addlinkedsrvlogin, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может для подключения к связанному серверу автоматически использовать учетные данные безопасности Windows (имя входа и пароль Windows) пользователя, выполняющего запрос. При этом должны выполняться следующие условия.  
  
-   Пользователь должен быть подключен к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме проверки подлинности Windows  
  
-   Делегирование учетной записи безопасности должно быть доступно на клиентском сервере и сервере-источнике  
  
-   Поставщик должен поддерживать режим проверки подлинности Windows; например [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], работающий в Windows  
  
> [!NOTE]  
>  Для одношаговых сценариев делегирование включать не обязательно, однако оно необходимо для многошаговых сценариев.  
  
 После завершения проверки подлинности связанным сервером (с помощью сопоставлений, заданных процедурой sp_addlinkedsrvlogin в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) разрешения на отдельные объекты в удаленной базе данных определяются связанным сервером, а не локальным.  
  
 Хранимую процедуру sp_addlinkedsrvlogin нельзя выполнять внутри пользовательских транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY LOGIN на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-connecting-all-local-logins-to-the-linked-server-by-using-their-own-user-credentials"></a>A. Все локальные имена входа подключаются к связанному серверу с собственными учетными данными  
 В следующем примере создается сопоставление, гарантирующее, что все имена входа на локальном сервере будут подключаться к связанному серверу `Accounts` с помощью собственных учетных данных.  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts';  
```  
  
 Или  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts', 'true';  
```  
  
> [!NOTE]  
>  Если для отдельных имен входа созданы явные сопоставления, то они имеют преимущество перед любыми глобальными сопоставлениями для данного связанного сервера.  
  
### <a name="b-connecting-a-specific-login-to-the-linked-server-by-using-different-user-credentials"></a>Б. Подключение указанного имени входа к связанному серверу с помощью других учетных данных  
 В следующем примере создается сопоставление, гарантирующее, что пользователь Windows `Domain\Mary` будет подключаться к связанному серверу `Accounts` с помощью имени входа `MaryP` и пароля `d89q3w4u`.  
  
```  
EXEC sp_addlinkedsrvlogin 'Accounts', 'false', 'Domain\Mary', 'MaryP', 'd89q3w4u';  
```  
  
> [!IMPORTANT]  
>  В этом примере проверка подлинности Windows не применяется. Пароли передаются в незашифрованном виде. Пароли могут быть видны в определениях источника данных и скриптах, сохраненных на диске и в составе резервных копий, а также в файлах журналов. Никогда не используйте для таких соединений пароль администратора. За инструкциями по безопасности среды обратитесь к сетевому администратору.  
  
## <a name="see-also"></a>См. также  
 [Представления каталога связанных серверов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
