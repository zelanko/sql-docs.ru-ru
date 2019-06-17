---
title: Настройка параметра конфигурации сервера "query governor cost limit" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], time to execute
- query governor cost limit option [SQL Server]
- time [SQL Server], query run time
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 758c2b42d09e120bf0621bcdedf26b93f130b39f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62786808"
---
# <a name="configure-the-query-governor-cost-limit-server-configuration-option"></a>Настройка параметра конфигурации сервера query governor cost limit
  В этом разделе описываются способы настройки `query governor cost limit` параметр конфигурации сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Используйте параметр предела стоимости регулятора запросов для того, чтобы задать верхнюю границу времени выполнения запроса. Цена запроса — это предполагаемое время в секундах, которое требуется для завершения запроса в конкретной конфигурации оборудования. Значение по умолчанию для этого параметра — 0, при котором регулятор запросов отключен. Это позволяет обрабатывать запросы без временных ограничений. Если задать значение больше нуля, регулятор запросов запрещает выполнение всех запросов, оценочная стоимость которых превышает это значение.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра query governor cost limit с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметру предельных затрат регулятора запросов](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Чтобы изменить значение параметра query governor cost limit для каждого соединения, используйте инструкцию [SET QUERY_GOVERNOR_COST_LIMIT](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql) .  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a>Настройка параметра query governor cost limit  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Перейдите на страницу **Соединения** .  
  
3.  Установите или снимите флажок **Использовать регулятор запросов для сокращения времени их выполнения** .  
  
     При установке этого флажка введите в поле внизу положительную величину, которую регулятор запросов использует для запрещения выполнения запросов со временем выполнения больше этой величины.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a>Настройка параметра query governor cost limit  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `query governor cost limit` равным `120` секундам.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметру предельных затрат регулятора запросов  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)](/sql/t-sql/statements/set-query-governor-cost-limit-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
