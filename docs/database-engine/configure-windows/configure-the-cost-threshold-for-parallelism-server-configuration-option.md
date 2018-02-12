---
title: "Параметр конфигурации сервера cost threshold for parallelism | Документы Майкрософт"
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
- cost threshold for parallelism option
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f81d5323ba6d967cd81b8fcf0382f32066168a1d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="configure-the-cost-threshold-for-parallelism-server-configuration-option"></a>Параметр конфигурации сервера cost threshold for parallelism
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **cost threshold for parallelism** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **cost threshold for parallelism** позволяет указать пороговое значение, при котором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает и выполняет параллельные планы для запросов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает и выполняет параллельный план для запроса только в случае, если оценочная стоимость выполнения последовательного плана для этого запроса выше значения, заданного параметром **cost threshold for parallelism**. Стоимость представляет предполагаемые затраты, необходимые для выполнения последовательного плана в определенной конфигурации оборудования (это не единица времени). Параметру **cost threshold for parallelism** можно присвоить любое значение от 0 до 32 767. Значение по умолчанию — 5.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра cost threshold for parallelism**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра стоимостного порога для параллелизма](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Стоимостью называется абстрактная единица себестоимости, а не единица ожидаемого времени. Устанавливайте параметр **cost threshold for parallelism** только на симметричных мультипроцессорах.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не учитывает значение параметра **cost threshold for parallelism** при следующих условиях.  
  
    -   В компьютере имеется только один логический процессор.  
  
    -   Только один логический процессор доступен для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в соответствии с параметром конфигурации **affinity mask** .  
  
    -   Параметру **max degree of parallelism** присвоено значение 1.  
  
 Логический процессор является базовой единицей процессора, которая позволяет операционной системе перенаправлять задачи или выполнить поток. Каждый логический процессор одновременно может выполнять только один поток. Процессорное ядро — это схема, которая обеспечивает возможность расшифровки и выполнения инструкций. Процессорное ядро может содержать один или более логических процессоров. Следующие запросы [!INCLUDE[tsql](../../includes/tsql-md.md)] можно использовать для получения сведений о ЦП системы.  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Это расширенный параметр, и изменять его следует только опытным администраторам баз данных или сертифицированным по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] специалистам.  
  
-   В определенных случаях может быть выбран параллельный план, даже если стоимость плана запроса меньше текущего значения параметра **cost threshold for parallelism** . Такое возможно, поскольку решение использовать параллельный или последовательный план основывается на ожидаемой стоимости, полученной до завершения полной оптимизации.  

-   Хотя значение по умолчанию (5) сохраняется для обратной совместимости, скорее всего, для существующих систем подойдет более высокое значение. Многие специалисты по SQL Server предлагают в качестве начальной точки значение 25 или 50, а также рекомендуют тестировать приложения с различными значениями для оптимизации производительности.
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a>Настройка параметра cost threshold for parallelism  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  В области **Параллелизм**измените параметр **CostThresholdForParallelism** на желаемое значение. Введите или выберите значение в диапазоне от 0 до 32767.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a>Настройка параметра cost threshold for parallelism  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `cost threshold for parallelism` равным `10`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра стоимостного порога для параллелизма  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md)   
 [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [Параметр конфигурации сервера «affinity mask»](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
