---
title: Параметр конфигурации сервера "Просмотр или настройка параметра сжатия резервных копий по умолчанию" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], backup compression default option
- backup compression [SQL Server], backup compression default Option
ms.assetid: 23029395-3e93-4c29-b7d6-e5a47a3526ff
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 40c603beaa8a9080c68b4c24494b2aff50aaf4f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100273"
---
# <a name="view-or-configure-the-backup-compression-default-server-configuration-option"></a>Параметр конфигурации сервера «Просмотр или настройка параметра сжатия резервных копий по умолчанию»
  В этой статье описываются способы просмотра и настройки параметра конфигурации сервера **backup compression default** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **backup compression default** определяет, будут ли сжатые резервные копии создаваться в экземплярах сервера по умолчанию. После установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр **backup compression default** отключен.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Просмотр и настройка параметра сжатия резервных копий по умолчанию с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение**  [после завершения настройки параметра backup compression default](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Сжатие резервных копий доступно не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   По умолчанию сжатие существенно повышает загрузку ЦП. Дополнительная нагрузка на ЦП может помешать выполнению других операций. Поэтому может потребоваться создать сжатые резервные копии с низким приоритетом в сеансе, для которого использование ЦП ограничивается [регулятором ресурсов](../../relational-databases/resource-governor/resource-governor.md). Дополнительные сведения см. ниже в подразделе [Использование регулятора ресурсов для ограничения загрузки ЦП при сжатии резервной копии (Transact-SQL)](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   При создании отдельной резервной копии, настройке конфигурации доставки журналов или создании плана обслуживания можно переопределить значения по умолчанию на уровне сервера.  
  
-   Сжатие резервной копии поддерживается как для дисковых устройств резервного копирования, так и для устройств резервного копирования на магнитной ленте.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-or-configure-the-backup-compression-default-option"></a>Просмотр и настройка параметра сжатия резервных копий по умолчанию  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Параметры базы данных** .  
  
3.  В окне **Резервное копирование и восстановление**поле **Сжатие резервных копий** показывает текущее значение параметра **backup compression default** . Данная настройка определяет поведение по умолчанию на уровне сервера сжатия резервных копий. Это выполняется следующим образом.  
  
    -   Если флажок **Сжатие резервных копий** сброшен, то новые резервные копии по умолчанию не сжимаются.  
  
    -   Если флажок **Сжатие резервных копий** установлен, то новые резервные копии по умолчанию сжимаются.  
  
     Члены предопределенной роли сервера **sysadmin** или **serveradmin** могут также изменить настройку по умолчанию, щелкнув поле **Сжатие резервных копий** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-the-backup-compression-default-option"></a>Просмотр параметров по умолчанию для сжатия резервных копий  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере выполняется запрос представления каталога [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) для определения значения для `backup compression default`. Значение, равное 0, указывает на отключение сжатия резервных копий, а значение, равное 1, указывает на включение сжатия резервных копий.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
SELECT value   
FROM sys.configurations   
WHERE name = 'backup compression default' ;  
GO  
  
```  
  
#### <a name="to-configure-the-backup-compression-default-option"></a>Настройка параметра сжатия резервных копий по умолчанию  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование хранимой процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для настройки на экземпляре сервера создания сжатых резервных копий по умолчанию.  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_configure 'backup compression default', 1 ;  
RECONFIGURE WITH OVERRIDE ;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Продолжение: после завершения настройки параметра backup compression default  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Общие сведения о резервном копировании (SQL Server)](../../relational-databases/backup-restore/backup-overview-sql-server.md)  
  
  
