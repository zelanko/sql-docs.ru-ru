---
title: Настройка параметра конфигурации сервера two digit year cutoff | Документация Майкрософт
description: Описание параметра two digit year cutoff. Сведения о том, как определяется способ, которым SQL Server преобразует двузначную запись года в четырехзначную.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- two digit year cutoff option
- four-digit years [SQL Server]
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8aa50fbd2eaa934c13704dc218084655c0f0f089
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764039"
---
# <a name="configure-the-two-digit-year-cutoff-server-configuration-option"></a>Настройка параметра конфигурации сервера two digit year cutoff
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **two digit year cutoff** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **two digit year cutoff** предназначен для указания целого числа в диапазоне от 1753 до 9999, которое представляет граничное значение при интерпретации года, указанного двумя цифрами. Временной промежуток по умолчанию для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] составляет 1950–2049, то есть пороговый год — 2049. Это означает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует двузначный год 49 как 2049, двузначный год 50 как 1950, а двузначный год 99 как 1999. Для поддержания обратной совместимости следует оставить этот параметр в значении по умолчанию.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра two digit year cutoff с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра two digit year cutoff](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Это расширенный параметр, и изменять его следует только опытным администраторам баз данных или сертифицированным по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] специалистам.  
  
-   Объекты автоматизации OLE используют значение 2030 в качестве порогового значения года для двузначной записи. Можно использовать параметр **two digit year cutoff** , чтобы обеспечить совместимость значений дат между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и клиентскими приложениями. 

-   Во избежание неоднозначности дат всегда используйте четырехзначные числа для обозначения лет в данных.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a>Настройка параметра two digit year cutoff  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Прочие параметры сервера** .  
  
3.  В области **Поддержка года из двух цифр**в поле **Если введено две цифры года**, **рассматривать их как год между** введите или выберите значение, которое будет конечным годом необходимого временного промежутка.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a>Настройка параметра two digit year cutoff  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `two digit year cutoff` равным `2030`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-two-digit-year-cutoff-option"></a><a name="FollowUp"></a> Дальнейшие действия. После настройки параметра two digit year cutoff  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  
