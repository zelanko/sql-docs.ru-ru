---
title: Настройка параметра конфигурации и сервера scan for startup procs | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- scan for startup procs option
ms.assetid: 6bf9d252-e766-458d-9dcd-23d895f032a2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 12bd68e17762a041e9d5c106f60d3e60e736750c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149034"
---
# <a name="configure-the-scan-for-startup-procs-server-configuration-option"></a>Настройка параметра конфигураци и сервера scan for startup procs
  В этом разделе описываются способы настройки параметра конфигурации сервера **scan for startup procs** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **scan for startup procs** предназначен для просмотра хранимых процедур, автоматически выполняемых при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если этому параметру присвоено значение 1, сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] просматривает и выполняет все автоматически запускаемые хранимые процедуры, которые определены на сервере. По умолчанию параметр **scan for startup procs** имеет значение 0 (не искать).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра scan for startup procs с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение**  [после настройки параметра scan for startup procs](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Значение этого параметра можно устанавливать с помощью процедуры **sp_configure**; однако оно будет задано автоматически, если используется процедура **sp_procoption**, применяемая для установки или снятия меток с автоматически выполняемых хранимых процедур. Если с помощью процедуры **sp_procoption** первая хранимая процедура помечается как автоматически выполняемая, этому параметру автоматически присваивается значение 1. Если процедура **sp_procoption** используется для снятия метки с последней хранимой процедуры как автоматически выполняемой, этому параметру автоматически присваивается значение 0. Если процедура **sp_procoption** используется для установления и снятия меток автоматически выполняемых процедур, а перед удалением процедур с них всегда снимаются метки автоматически выполняемых, нет необходимости устанавливать этот параметр вручную.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a>Настройка параметра scan for startup procs  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  В разделе **Разное**для параметра **Scan for Startup Procs** выберите значение True или False в раскрывающемся списке.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-scan-for-startup-procs-option"></a>Настройка параметра scan for startup procs  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `scan for startup procs` равным `1`.  
  
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
  
## <a name="see-also"></a>См. также  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [sp_procoption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql)  
  
  
