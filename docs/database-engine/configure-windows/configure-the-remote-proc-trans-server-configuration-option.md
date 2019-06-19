---
title: Настройка параметра конфигурации сервера remote proc trans
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote proc trans option
- distributed transactions [SQL Server], enforcing
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 373cf5287228ba39d97235e4de23503c07024dd0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799102"
---
# <a name="configure-the-remote-proc-trans-server-configuration-option"></a>Настройка параметра конфигурации сервера remote proc trans
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **remote proc trans** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **remote proc trans** предназначен для защиты действий межсерверной процедуры с помощью транзакции координатора распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC).  
  
 Установите значение параметра **remote proc trans** равным 1, чтобы применить распределенную транзакцию координатора MS DTC, защищающую свойства ACID (atomic, consistent, isolated, durable — атомарность, согласованность, изолированность, надежность) транзакций. Сеансы, начатые после установки этого параметра в 1, наследуют значение этого параметра в качестве значения по умолчанию.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра remote proc trans с помощью различных средств**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра remote proc trans](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Это значение можно установить только при разрешенных соединениях с удаленными серверами.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр предоставляется в целях совместимости с предыдущими версиями [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для приложений, использующих удаленные хранимые процедуры. Вместо вызовов удаленных хранимых процедур используйте распределенные запросы, которые ссылаются на связанные серверы, определенные с помощью процедуры [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a>Настройка параметра remote proc trans  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Выберите узел **Соединения** .  
  
3.  В области **Удаленные серверные соединения**установите флажок **Требовать распределенных транзакций для межсерверных соединений** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a>Настройка параметра remote proc trans  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `remote proc trans` равным `1`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра remote proc trans  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
