---
title: "Настройка параметра конфигурации сервера \"min memory per query\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e49ed68ce5e3f4621017db6cd09d2eec680b77f2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>Настройка параметра конфигурации сервера min memory per query
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **min memory per query** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **min memory per query** определяет минимальный объем памяти (в килобайтах), выделяемый для выполнения запроса. Например, если параметру **min memory per query** присвоено значение, равное 2048 КБ, запрос гарантированно получит указанный объем памяти. Значение по умолчанию — 1 024 КБ. Минимальное значение — 512 КБ, максимальное — 2 147 483 647 KB (2 ГБ).  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра min memory per query с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение:**  [после настройки параметра min memory per query](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Параметр min memory per query имеет преимущество перед параметром [index create memory](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md). Если изменяются оба параметра и значение параметра index create memory меньше значения min memory per query, то в системе отобразится предупреждающее сообщение, но это значение будет установлено. При выполнении запроса будет выдано еще одно аналогичное предупреждение.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Обработчик запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается определить оптимальный объем памяти, выделяемой запросу. Параметр min memory per query позволяет администратору указать минимальный размер памяти, который получает каждый запрос. Запросы обычно получают объем памяти больше указанного значения, если выполняют хэширование или сортировку больших объемов данных. Увеличение значения параметра min memory per query может повысить производительность для малых и средних запросов, однако это может привести к повышению конкуренции за память. Параметр min memory per query включает память, выделенную для сортировки.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Настройка параметра min memory per query  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Память** .  
  
3.  В поле **Минимальный объем памяти для запроса** введите минимальный объем памяти (в килобайтах), который будет выделен запросу для выполнения.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Настройка параметра min memory per query  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано использование хранимой процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `min memory per query` равным `3500` КБ.  
  
```tsql  
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
  
##  <a name="FollowUp"></a> Продолжение: после настройки параметра min memory per query  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md)  
  
  

