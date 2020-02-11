---
title: Удаленные серверы | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], remote servers
- remote servers [SQL Server], configuring
- remote servers [SQL Server]
- servers [SQL Server], remote
- remote access option
ms.assetid: abf0fa24-f199-4273-9a1a-e8787ac9bee1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e8fd1464857b77139ca0bef310eee8be949d77cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809879"
---
# <a name="remote-servers"></a>Удаленные серверы
  Удаленные серверы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются лишь для обратной совместимости. Новые приложения должны использовать вместо них связанные серверы. Дополнительные сведения см. в разделе [Связанные серверы (компонент Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md).  
  
 Настройка удаленного сервера позволяет клиенту, подключившемуся к одному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполнить хранимую процедуру на другом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не устанавливая отдельное соединение. Вместо этого сервер, к которому подключен клиент, принимает запрос клиента и отправляет запрос удаленному серверу от имени клиента. Удаленный сервер обрабатывает запрос и возвращает результаты исходному серверу. Этот сервер, в свою очередь, передает результаты клиенту. При настройке удаленных серверов необходимо учитывать требования обеспечения безопасности.  
  
 Если требуется настроить серверы таким образом, чтобы хранимые процедуры выполнялись на другом сервере, и при этом не существует уже выполненной настройки удаленных серверов, используйте связанные сервера вместо удаленных серверов. Связанные сервера поддерживают выполнение и хранимых процедур, и распределенных запросов; в то же время удаленные сервера поддерживают только хранимые процедуры.  
  
## <a name="remote-server-details"></a>Подробности использования удаленных серверов  
 Удаленные сервера настраиваются парами. Чтобы настроить пару удаленных серверов, нужно настроить оба сервера таким образом, чтобы они являлись удаленными серверами друг для друга.  
  
 Обычно устанавливать параметры конфигурации удаленных серверов не требуется. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Set задает параметры по умолчанию для локальных и удаленных компьютеров, чтобы разрешить соединения с удаленным сервером.  
  
 Для функционирования доступа к удаленному серверу требуется, чтобы параметр конфигурации **remote access** был установлен в 1 как на локальном, так и на удаленном компьютерах. Параметр  **remote access** управляет возможностью подключений с удаленных серверов (это значение по умолчанию). Этот параметр можно сбросить, воспользовавшись хранимой процедурой [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_configure** или же средой [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Чтобы установить параметр в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]на странице **Свойства соединений с серверами** , используйте возможность **Разрешить удаленные соединения с этим сервером**. Чтобы открыть вкладку **Свойства соединений с сервером** , в обозревателе объектов щелкните имя сервера правой кнопкой мыши и выберите **Свойства**. В окне **Свойства сервера** выберите вкладку **Соединения** .  
  
 На этой вкладке можно отключить удаленную настройку сервера, чтобы запретить доступ к локальному серверу пользователям удаленного сервера, с которым он составляет пару.  
  
## <a name="security-for-remote-servers"></a>Безопасность удаленных серверов  
 Чтобы включить вызовы по протоколу RPC для удаленного сервера, необходимо настроить сопоставления имен входа на удаленном сервере и, возможно, на локальном сервере, где запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию вызовы удаленных процедур (RPC) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]отключены. Такая конфигурация усиливает безопасность сервера, уменьшая его подверженную атакам контактную зону. Перед использованием RPC необходимо включить эту функцию. Дополнительные сведения см. в разделе [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
### <a name="setting-up-the-remote-server"></a>Настройка удаленного сервера  
 Сопоставления удаленных имен входа должны быть настроены на удаленном сервере. При помощи данных сопоставлений удаленный сервер привязывает входящее имя входа соединения RPC от определенного сервера к локальному имени входа. Сопоставления удаленных имен входа могут быть установлены при помощи хранимой процедуры **sp_addremotelogin** на удаленном сервере.  
  
> [!NOTE]  
>  Параметр **trusted** процедуры  **sp_remoteoption** не поддерживается в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="setting-up-the-local-server"></a>Настройка локального сервера  
 Для локальных имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , прошедших проверку подлинности, устанавливать сопоставление имен входа на локальном сервере не нужно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]использует локальное имя входа и пароль для подключения к удаленному серверу. Для имен входа, прошедших проверку подлинности Windows, настройте сопоставление локальных имен входа, определяющее пароль и имя входа, используемые экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при создании подключения RPC к удаленному серверу.  
  
 Для имен входа, созданных проверкой подлинности Windows, необходимо создать сопоставление имени входа и пароля при помощи хранимой процедуры **sp_addlinkedservlogin** . Данное имя входа и пароль должны совпадать с входящим именем входа и паролем, представленными удаленным сервером и созданными процедурой **sp_addremotelogin**.  
  
> [!NOTE]  
>  По возможности используйте аутентификацию Windows.  
  
### <a name="remote-server-security-example"></a>Пример системы безопасности удаленного сервера  
 Проверьте следующие установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **serverSend** и **serverReceive**. **serverReceive** настроен на отображение входящего входа из **serverSend**, именуемого **Sales_Mary**, в имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , прошедшее проверку подлинности, в **serverReceive**, именуемое **Алисой**. Другое входящее имя входа из **serverSend**, именуемое **Джо**, сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с аутентифицированным именем входа в **serverReceive**_,_ именуемым **Joe**.  
  
 В следующем примере кода Transact-SQL `serverSend` настраивается на выполнение вызовов RPC по отношению к `serverReceive`.  
  
```  
--Create remote server entry for RPCs   
--from serverSend in serverReceive.  
EXEC sp_addserver 'serverSend';  
GO  
  
--Create remote login mapping for login 'Sales_Mary' from serverSend  
--to Alice.  
EXEC sp_addremotelogin 'serverSend', 'Alice', 'Sales_Mary';  
GO  
--Create remote login mapping for login Joe from serverReceive   
--to same login.  
--Assumes same password for Joe in both servers.  
EXEC sp_addremotelogin 'serverSend', 'Joe', 'Joe';  
GO  
```  
  
 В `serverSend`сопоставление местного имени входа создается для имени входа `Sales\Mary` , прошедшего проверку подлинности Windows, и имени входа `Sales_Mary`. Для имени входа `Joe`локальное сопоставление не требуется, так как по умолчанию используются одинаковые имена входа и пароли, и `serverReceive` уже обладает сопоставлением для `Joe`.  
  
```  
--Create a remote server entry for RPCs from serverReceive.  
EXEC sp_addserver 'serverReceive';  
GO  
--Create a local login mapping for the Windows authenticated login.  
--Sales\Mary to Sales_Mary. The password should match the  
--password for the login Sales_Mary in serverReceive.  
EXEC sp_addlinkedsrvlogin 'serverReceive', false, 'Sales\Mary',  
   'Sales_Mary', '430[fj%dk';  
GO  
```  
  
## <a name="viewing-local-or-remote-server-properties"></a>Просмотр свойств локального или удаленного сервера  
 Для просмотра атрибутов локальных и удаленных серверов можно использовать расширенную хранимую процедуру **xp_msver** . В список этих атрибутов входят: номер версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], тип и число процессоров компьютера и версия операционной системы. С локального сервера можно просматривать базы данных, файлы, имена входа и инструменты удаленного сервера. Дополнительные сведения см. в статье [xp_msver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql).  
  
## <a name="related-tasks"></a>Связанные задачи  
 [&#40;ядро СУБД связанных серверов&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)  
  
## <a name="related-content"></a>См. также  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 [Настройка параметра конфигурации сервера remote access](configure-the-remote-access-server-configuration-option.md)  
  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
