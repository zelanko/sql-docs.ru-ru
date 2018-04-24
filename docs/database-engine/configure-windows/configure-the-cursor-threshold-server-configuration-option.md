---
title: Настройка параметра конфигурации сервера "cursor threshold" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cursor threshold option
ms.assetid: 189f2067-c6c4-48bd-9bd9-65f6b2021c12
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1435afb0c27222ccc5877b30712571959032420e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="configure-the-cursor-threshold-server-configuration-option"></a>Настройка параметра конфигурации сервера cursor threshold
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описывается настройка параметра конфигурации сервера **cursor threshold** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **cursor threshold** используется для указания количества строк в наборе курсора, при котором наборы ключей курсора создаются асинхронно. Когда курсоры формируют набор ключей для результирующего набора, оптимизатор запросов прогнозирует количество строк, которые будут возвращены для этого результирующего набора. Если оптимизатор запросов определяет, что число возвращенных строк превышает указанное пороговое значение, курсор формируется асинхронно, позволяя пользователю извлекать из него строки при продолжающемся процессе его заполнения. В противном случае курсор формируется синхронно, и запрос ожидает, пока не будут возвращены все строки.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра cursor threshold с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение**  [после настройки параметра cursor threshold](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает асинхронное формирование управляемых набором ключей или статических курсоров [!INCLUDE[tsql](../../includes/tsql-md.md)] . [!INCLUDE[tsql](../../includes/tsql-md.md)] (такие как OPEN или FETCH) пакетированы, поэтому нет необходимости в асинхронном формировании курсоров [!INCLUDE[tsql](../../includes/tsql-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] продолжает поддерживать асинхронные курсоры, управляемые набором ключей, а также статические серверные курсоры API. При этом выполнение инструкции OPEN производится с небольшой задержкой, так как при каждой операции над курсором клиент осуществляет обмен данными с сервером.  
  
-   Точность определения приблизительного количества строк в наборе ключей зависит от валюты, используемой в статистике по каждой таблице курсора с помощью оптимизатора запросов.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Это расширенный параметр, и изменять его следует только опытным администраторам баз данных или сертифицированным по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] специалистам.  
  
-   Если значение параметра **cursor threshold** установить равным -1, все наборы ключей будут создаваться синхронно, что предпочтительно для небольших наборов курсоров. Если значение параметра **cursor threshold** установить равным 0, все наборы ключей будут создаваться асинхронно. При других значениях оптимизатор запросов сравнивает количество предполагаемых строк в наборе курсора и формирует набор ключей асинхронно, если значение превышает число, заданное параметром **cursor threshold**. Не следует присваивать параметру **cursor threshold** слишком низкое значение, поскольку небольшие результирующие наборы предпочтительно формировать в синхронном режиме.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-cursor-threshold-option"></a>Настройка параметра cursor threshold  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  В области **Разное**установите для параметра **Порог курсора** необходимое значение.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-cursor-threshold-option"></a>Настройка параметра cursor threshold  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование хранимой процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `cursor threshold` равным `0` , при котором наборы ключей курсора формируются асинхронно.  
  
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
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Продолжение: после настройки параметра cursor threshold  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [@@CURSOR_ROWS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-rows-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)  
  
  
