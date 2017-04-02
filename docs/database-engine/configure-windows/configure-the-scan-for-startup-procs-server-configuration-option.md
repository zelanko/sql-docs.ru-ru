---
title: "Настройка параметра конфигураци и сервера scan for startup procs | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "параметр scan for startup procs"
ms.assetid: 6bf9d252-e766-458d-9dcd-23d895f032a2
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Настройка параметра конфигураци и сервера scan for startup procs
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **scan for startup procs** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **scan for startup procs** предназначен для просмотра хранимых процедур, автоматически выполняемых при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если этому параметру присвоено значение 1, сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] просматривает и выполняет все автоматически запускаемые хранимые процедуры, которые определены на сервере. По умолчанию параметр **scan for startup procs** имеет значение 0 (не искать).  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра scan for startup procs с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение**  [после настройки параметра scan for startup procs](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Значение этого параметра можно устанавливать с помощью процедуры **sp_configure**; однако оно будет задано автоматически, если используется процедура **sp_procoption**, применяемая для установки или снятия меток с автоматически выполняемых хранимых процедур. Если с помощью процедуры **sp_procoption** первая хранимая процедура помечается как автоматически выполняемая, этому параметру автоматически присваивается значение 1. Если процедура **sp_procoption** используется для снятия метки с последней хранимой процедуры как автоматически выполняемой, этому параметру автоматически присваивается значение 0. Если процедура **sp_procoption** используется для установления и снятия меток автоматически выполняемых процедур, а перед удалением процедур с них всегда снимаются метки автоматически выполняемых, нет необходимости устанавливать этот параметр вручную.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Настройка параметра scan for startup procs  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  В разделе **Разное** для параметра **Scan for Startup Procs** выберите значение True или False в раскрывающемся списке.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Настройка параметра scan for startup procs  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `scan for startup procs` равным `1`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'scan for startup procs', 1 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
##  <a name="FollowUp"></a> Продолжение: после настройки параметра scan for startup procs  
 Чтобы изменения вступили в силу, необходимо перезапустить сервер.  
  
## См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_procoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-procoption-transact-sql.md)  
  
  