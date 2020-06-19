---
title: Настройка параметра конфигурации сервера "cursor threshold" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cursor threshold option
ms.assetid: 189f2067-c6c4-48bd-9bd9-65f6b2021c12
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0d7fd9ecafda270a02f1fba9f5dd74adc9e299d1
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935745"
---
# <a name="configure-the-cursor-threshold-server-configuration-option"></a>Настройка параметра конфигурации сервера cursor threshold
  В этом разделе описывается настройка параметра конфигурации сервера **cursor threshold** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **cursor threshold** используется для указания количества строк в наборе курсора, при котором наборы ключей курсора создаются асинхронно. Когда курсоры формируют набор ключей для результирующего набора, оптимизатор запросов прогнозирует количество строк, которые будут возвращены для этого результирующего набора. Если оптимизатор запросов определяет, что число возвращенных строк превышает указанное пороговое значение, курсор формируется асинхронно, позволяя пользователю извлекать из него строки при продолжающемся процессе его заполнения. В противном случае курсор формируется синхронно, и запрос ожидает, пока не будут возвращены все строки.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра cursor threshold с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра cursor threshold](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает асинхронное формирование управляемых набором ключей или статических курсоров [!INCLUDE[tsql](../../includes/tsql-md.md)] . [!INCLUDE[tsql](../../includes/tsql-md.md)] (такие как OPEN или FETCH) пакетированы, поэтому нет необходимости в асинхронном формировании курсоров [!INCLUDE[tsql](../../includes/tsql-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] продолжает поддерживать асинхронные курсоры, управляемые набором ключей, а также статические серверные курсоры API. При этом выполнение инструкции OPEN производится с небольшой задержкой, так как при каждой операции над курсором клиент осуществляет обмен данными с сервером.  
  
-   Точность определения приблизительного количества строк в наборе ключей зависит от валюты, используемой в статистике по каждой таблице курсора с помощью оптимизатора запросов.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Если значение параметра **cursor threshold** установить равным -1, все наборы ключей будут создаваться синхронно, что предпочтительно для небольших наборов курсоров. Если значение параметра **cursor threshold** установить равным 0, все наборы ключей будут создаваться асинхронно. При других значениях оптимизатор запросов сравнивает количество предполагаемых строк в наборе курсора и формирует набор ключей асинхронно, если значение превышает число, заданное параметром **cursor threshold**. Не следует присваивать параметру **cursor threshold** слишком низкое значение, поскольку небольшие результирующие наборы предпочтительно формировать в синхронном режиме.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-cursor-threshold-option"></a>Настройка параметра cursor threshold  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  В области **Разное**установите для параметра **Порог курсора** необходимое значение.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-cursor-threshold-option"></a>Настройка параметра cursor threshold  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование хранимой процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `cursor threshold` равным `0` , при котором наборы ключей курсора формируются асинхронно.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cursor threshold', 0 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-cursor-threshold-option"></a><a name="FollowUp"></a> Дальнейшие действия. После настройки параметра cursor threshold  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [@@CURSOR_ROWS (Transact-SQL)](/sql/t-sql/functions/cursor-rows-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [UPDATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
