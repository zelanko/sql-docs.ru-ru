---
title: Настройка параметра конфигурации сервера "min memory per query" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: dfee7265529419aecf2b05831503ed134b93f525
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62787064"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>Настройка параметра конфигурации сервера min memory per query
  В этом разделе описывается настройка параметра конфигурации `min memory per query` сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или. [!INCLUDE[tsql](../../includes/tsql-md.md)] `min memory per query` Параметр задает минимальный объем памяти (в килобайтах), который будет выделен для выполнения запроса. Например, если `min memory per query` для задано значение 2 048 КБ, то запрос гарантированно получит по крайней мере такой большой объем памяти. Значение по умолчанию — 1 024 КБ. Минимальное значение — 512 КБ, максимальное — 2 147 483 647 KB (2 ГБ).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра min memory per query с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение:**  [после настройки параметра min memory per query](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Уровень минимального объема памяти для запроса имеет приоритет над [параметром индекс создания памяти](configure-the-index-create-memory-server-configuration-option.md). Если изменяются оба параметра и значение параметра index create memory меньше значения min memory per query, то в системе отобразится предупреждающее сообщение, но это значение будет установлено. При выполнении запроса будет выдано еще одно аналогичное предупреждение.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Обработчик запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается определить оптимальный объем памяти, выделяемой запросу. Параметр min memory per query позволяет администратору указать минимальный размер памяти, который получает каждый запрос. Запросы обычно получают объем памяти больше указанного значения, если выполняют хэширование или сортировку больших объемов данных. Увеличение значения параметра min memory per query может повысить производительность для малых и средних запросов, однако это может привести к повышению конкуренции за память. Параметр min memory per query включает память, выделенную для сортировки.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Настройка параметра min memory per query  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Память** .  
  
3.  В поле **Минимальный объем памяти для запроса** введите минимальный объем памяти (в килобайтах), который будет выделен запросу для выполнения.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Настройка параметра min memory per query  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано использование хранимой процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `min memory per query` равным `3500` КБ.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-min-memory-per-query-option"></a><a name="FollowUp"></a>Дальнейшие действия. После настройки параметра мин. памяти на запрос  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Настройка параметра конфигурации сервера index create memory](configure-the-index-create-memory-server-configuration-option.md)  
  
  
