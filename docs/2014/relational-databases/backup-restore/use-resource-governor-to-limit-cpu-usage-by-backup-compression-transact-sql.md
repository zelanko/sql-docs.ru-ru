---
title: Использование регулятора ресурсов для ограничения загрузки ЦП при сжатии резервной копии (компонент Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backup compression [SQL Server], Resource Governor
- backup compression [SQL Server], CPU usage
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- Resource Governor, backup compression
ms.assetid: 01796551-578d-4425-9b9e-d87210f7ba72
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bc9e5e2f75d253e45a11d88fe9fbf6c527b71d03
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283490"
---
# <a name="use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql"></a>Использование регулятора ресурсов для ограничения загрузки ЦП при сжатии резервной копии (компонент Transact-SQL)
  По умолчанию резервное копирование с использованием сжатия существенно увеличивает загрузку ЦП, а дополнительная загрузка ЦП процессом сжатия может неблагоприятно повлиять на параллельные операции. Поэтому может понадобиться создать низкоприоритетную сжатую резервную копию в сеансе, загрузка ЦП в котором ограничивается[Resource Governor](../resource-governor/resource-governor.md) в случае конфликта ЦП. В этом разделе представлен сценарий, классифицирующий сеансы отдельного пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем сопоставления их с той или иной группой рабочей нагрузки регулятора ресурсов, которая в таких случаях ограничивает загрузку ЦП.  
  
> [!IMPORTANT]  
>  В данном сценарии регулятора ресурсов классификация сеансов может основываться на имени пользователя, названии приложения или каком-либо другом критерии различения соединения. Дополнительные сведения см. в разделах [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) и [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md).  
  
##  <a name="Top"></a> Этот раздел содержит следующий набор сценариев, представленных в следующей последовательности.  
  
1.  [Создание учетной записи и пользователя для операций с низким приоритетом](#setup_login_and_user)  
  
2.  [Настройка регулятора ресурсов для ограничения загрузки ЦП](#configure_RG)  
  
3.  [Проверка классификации текущего сеанса (Transact-SQL)](#verifying)  
  
4.  [Сжатие резервных копий в сеансе с ограничением доступа к ЦП](#creating_compressed_backup)  
  
##  <a name="setup_login_and_user"></a> Создание учетной записи и пользователя для операций с низким приоритетом  
 Для сценария в этом разделе требуется низкоприоритетное имя входа в систему [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пользователь. Имя пользователя будет использоваться для классификации сеансов, запущенных в процессе входа, и для направления их в группу рабочей нагрузки регулятора ресурсов, которая ограничивает загрузку ЦП.  
  
 Ниже описываются этапы настройки имени для входа и пользователя для этой цели, за которыми следует пример на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] — "Пример А. Настройка имени входа и пользователя (Transact-SQL)".  
  
### <a name="to-set-up-a-login-and-database-user-for-classifying-sessions"></a>Настройка имени входа и пользователя базы данных для классификации сеансов  
  
1.  Создайте имя входа на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для создания низкоприоритетных сжатых резервных копий.  
  
     **Создание имени входа**  
  
    -   [Создание имени для входа](../security/authentication-access/create-a-login.md)  
  
    -   [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)  
  
2.  При необходимости можно также предоставить этому имени входа разрешение VIEW SERVER STATE.  
  
    -   [GRANT, предоставление разрешения на системный объект (Transact-SQL)](/sql/t-sql/statements/grant-system-object-permissions-transact-sql)  
  
     Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на участника базы данных (Transact-SQL)](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).  
  
3.  Создайте пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для данного имени входа.  
  
     **Создание пользователя**  
  
    -   [Создание пользователя базы данных](../security/authentication-access/create-a-database-user.md)  
  
    -   [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)  
  
4.  Чтобы разрешить для сеансов данного имени входа и пользователя резервное копирование заданной базы данных, добавьте пользователя к роли db_backupoperator для этой базы данных. Выполните это для каждой из баз данных, резервные копии которых должен создать данный пользователь. При необходимости добавьте пользователя к другим предопределенным ролям баз данных.  
  
     **Добавление пользователя к предопределенной роли базы данных**  
  
    -   [Хранимая процедура sp_addrolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)  
  
     Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на участника базы данных (Transact-SQL)](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).  
  
### <a name="example-a-setting-up-a-login-and-user-transact-sql"></a>Пример А. Настройка имени входа и пользователя (Transact-SQL)  
 Следующий пример касается только случая, когда выбрано создание нового имени входа и пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для низкоприоритетных резервных копий. В качестве альтернативы можно использовать существующие имя входа и пользователя, если таковой существует.  
  
> [!IMPORTANT]  
>  В приведенном ниже примере используется образец имени для входа и пользователя — *имя_домена*`\MAX_CPU`. Замените их именами входа и пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые планируется использовать при создании низкоприоритетных сжатых резервных копий.  
  
 В этом примере создается имя для входа для учетной записи Windows *имя_домена*`\MAX_CPU` , а затем этому имени для входа предоставляется разрешение VIEW SERVER STATE. Это разрешение позволяет проверить классификацию сеансов имени входа в регуляторе ресурсов. Затем для имени *имя_домена*`\MAX_CPU` создается пользователь и добавляется к предопределенной роли db_backupoperator для образца базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . Это имя пользователя будет использоваться функцией-классификатором в регуляторе ресурсов.  
  
```tsql  
-- Create a SQL Server login for low-priority operations  
USE master;  
CREATE LOGIN [domain_name\MAX_CPU] FROM WINDOWS;  
GRANT VIEW SERVER STATE TO [domain_name\MAX_CPU];  
GO  
-- Create a SQL Server user in AdventureWorks2012 for this login  
USE AdventureWorks2012;  
CREATE USER [domain_name\MAX_CPU] FOR LOGIN [domain_name\MAX_CPU];  
EXEC sp_addrolemember 'db_backupoperator', 'domain_name\MAX_CPU';  
GO  
  
```  
  
 [&#91;В начало&#93;](#Top)  
  
##  <a name="configure_RG"></a> Настройка регулятора ресурсов для ограничения загрузки ЦП  
  
> [!NOTE]  
>  Убедитесь, что регулятор ресурсов включен. Дополнительные сведения см. в разделе [Активация регулятора ресурсов](../resource-governor/enable-resource-governor.md).  
  
 В этом сценарии регулятора ресурсов процесс настройки состоит из следующих основных этапов.  
  
1.  Создайте и настройте для регулятора ресурсов пул ресурсов, который ограничивает максимальную среднюю пропускную способность ЦП, предоставляемую запросам из пула ресурсов в случае состязания из-за ЦП.  
  
2.  Создайте и настройте группу рабочей нагрузки регулятора ресурсов, которая будет использовать этот пул.  
  
3.  Создайте *функцию-классификатор*— определяемую пользователем функцию, возвращаемые значения которой используются регулятором Resource Governor для классификации сеансов с целью направления в соответствующую группу рабочей нагрузки.  
  
4.  Зарегистрируйте эту функцию-классификатор в регуляторе ресурсов.  
  
5.  Примените изменения в хранящейся в памяти конфигурации регулятора ресурсов.  
  
> [!NOTE]  
>  Сведения о пулах ресурсов Resource Governor, группах рабочей нагрузки и классификации см. в разделе [Resource Governor](../resource-governor/resource-governor.md).  
  
 Инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] для указанных этапов описаны в процедуре «Настройка регулятора ресурсов для ограничения загрузки ЦП», за которой следует пример процедуры на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **Настройка регулятора ресурсов (среда SQL Server Management Studio)**  
  
-   [Настройка регулятора ресурсов с помощью шаблона](../resource-governor/configure-resource-governor-using-a-template.md)  
  
-   [Создание пула ресурсов](../resource-governor/create-a-resource-pool.md)  
  
-   [Создание группы рабочей нагрузки](../resource-governor/create-a-workload-group.md)  
  
### <a name="to-configure-resource-governor-for-limiting-cpu-usage-transact-sql"></a>Настройка регулятора ресурсов для ограничения загрузки ЦП (Transact-SQL)  
  
1.  Выполните инструкцию [CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) , чтобы создать пул ресурсов. В примере этой процедуры используется следующий синтаксис:  
  
     *CREATE RESOURCE POOL имя_пула* WITH ( MAX_CPU_PERCENT = *значение* );  
  
     *Value* — целое число от 1 до 100, которое указывает максимальную среднюю пропускную способность ЦП в процентах. Рекомендуемое значение зависит от конкретной среды. Для иллюстрации в примере из этого разделе используется значение 20% (MAX_CPU_PERCENT = 20).  
  
2.  Выполните инструкцию [CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) , чтобы создать группу рабочей нагрузки для низкоприоритетных операций, загрузку ЦП которыми следует регулировать. В примере этой процедуры используется следующий синтаксис:  
  
     CREATE WORKLOAD GROUP *имя_группы* USING *имя_пула*;  
  
3.  Выполните инструкцию [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) , чтобы создать функцию-классификатор, сопоставляющую созданную на предыдущем этапе группу рабочей нагрузки с пользователем с низкоприоритетным именем входа. В примере этой процедуры используется следующий синтаксис:  
  
     CREATE FUNCTION [*имя_схемы*.]*имя_функции*() RETURNS sysname  
  
     WITH SCHEMABINDING  
  
     AS  
  
     BEGIN  
  
     DECLARE @workload_group_name AS *sysname*  
  
     IF (SUSER_NAME() = '*пользователь_с_низкоприоритетным_именем_входа*')  
  
     SET @workload_group_name = '*workload_group_name*'  
  
     RETURN @workload_group_name  
  
     END  
  
     Дополнительные сведения о компонентах этой инструкции CREATE FUNCTION см. в разделах:  
  
    -   [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
    -   [SUSER_SNAME (Transact-SQL)](/sql/t-sql/functions/suser-sname-transact-sql)  
  
        > [!IMPORTANT]  
        >  SUSER_NAME — лишь одна из нескольких системных функций, которые можно использовать в функции-классификаторе. Дополнительные сведения см. в разделе [Создание и проверка определяемой пользователем функции-классификатора](../resource-governor/create-and-test-a-classifier-user-defined-function.md).  
  
    -   [SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql).  
  
4.  Выполните инструкцию [ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) , чтобы зарегистрировать функцию-классификатор в регуляторе ресурсов. В примере этой процедуры используется следующий синтаксис:  
  
     ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *имя_схемы*.*имя_функции*);  
  
5.  Выполните еще одну инструкцию ALTER RESOURCE GOVERNOR, чтобы применить изменения в хранящейся в памяти конфигурации регулятора ресурсов, как указано ниже:  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE;  
    ```  
  
### <a name="example-b-configuring-resource-governor-transact-sql"></a>Пример Б. Настройка регулятора ресурсов (Transact-SQL)  
 В нижеприведенном примере в одной транзакции выполняются следующие шаги.  
  
1.  Создание пула ресурсов `pMAX_CPU_PERCENT_20` .  
  
2.  Создание группы рабочей нагрузки `gMAX_CPU_PERCENT_20` .  
  
3.  Создание функции-классификатора `rgclassifier_MAX_CPU()` , в которой используется имя пользователя, созданное в предыдущем примере.  
  
4.  Регистрация функции-классификатора в регуляторе ресурсов.  
  
 После того как транзакция зафиксирована, применяются изменения в конфигурации, запрошенные в инструкциях ALTER WORKLOAD GROUP или ALTER RESOURCE POOL.  
  
> [!IMPORTANT]  
>  В приведенном ниже примере используется образец имени пользователя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , созданный в разделе "Пример А. Настройка имени входа и пользователя (Transact-SQL)", *имя_домена*`\MAX_CPU`. Замените его именем пользователя, соответствующего имени входа, которое планируется использовать для создания низкоприоритетных сжатых резервных копий.  
  
```tsql  
-- Configure Resource Governor.  
BEGIN TRAN  
USE master;  
-- Create a resource pool that sets the MAX_CPU_PERCENT to 20%.   
CREATE RESOURCE POOL pMAX_CPU_PERCENT_20  
   WITH  
      (MAX_CPU_PERCENT = 20);  
GO  
-- Create a workload group to use this pool.   
CREATE WORKLOAD GROUP gMAX_CPU_PERCENT_20  
USING pMAX_CPU_PERCENT_20;  
GO  
-- Create a classification function.  
-- Note that any request that does not get classified goes into   
-- the 'Default' group.  
CREATE FUNCTION dbo.rgclassifier_MAX_CPU() RETURNS sysname   
WITH SCHEMABINDING  
AS  
BEGIN  
    DECLARE @workload_group_name AS sysname  
      IF (SUSER_NAME() = 'domain_name\MAX_CPU')  
          SET @workload_group_name = 'gMAX_CPU_PERCENT_20'  
    RETURN @workload_group_name  
END;  
GO  
  
-- Register the classifier function with Resource Governor.  
ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION= dbo.rgclassifier_MAX_CPU);  
COMMIT TRAN;  
GO  
-- Start Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
 [&#91;В начало&#93;](#Top)  
  
##  <a name="verifying"></a> Проверка классификации текущего сеанса (Transact-SQL)  
 При необходимости войдите в систему как пользователь, указанный в функции-классификаторе, и проверьте классификацию сеанса, выполнив следующую инструкцию [SELECT](/sql/t-sql/queries/select-transact-sql) в обозревателе объектов:  
  
```tsql  
USE master;  
SELECT sess.session_id, sess.login_name, sess.group_id, grps.name   
FROM sys.dm_exec_sessions AS sess   
JOIN sys.dm_resource_governor_workload_groups AS grps   
    ON sess.group_id = grps.group_id  
WHERE session_id > 50;  
GO  
```  
  
 В области результатов столбец **name** должен содержать один или несколько сеансов для имени группы рабочей нагрузки, указанного в функции-классификаторе.  
  
> [!NOTE]  
>  Дополнительные сведения о динамических административных представлениях, вызываемых этой инструкцией SELECT, см. в разделах [sys.dm_exec_sessions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) и [sys.dm_resource_governor_workload_groups (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql).  
  
 [&#91;В начало&#93;](#Top)  
  
##  <a name="creating_compressed_backup"></a> Сжатие резервных копий в сеансе с ограничением доступа к ЦП  
 Чтобы создать сжатую резервную копию в сеансе с ограниченной максимальной загрузкой ЦП, войдите в систему как пользователь, указанный в функции-классификаторе. В команде резервного копирования укажите предложение WITH COMPRESSION ([!INCLUDE[tsql](../../includes/tsql-md.md)]) или выберите вариант **Сжимать резервные копии** ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]). Сведения о создании сжатой резервной копии базы данных см. в разделе [Создание полной резервной копии базы данных (SQL Server)](create-a-full-database-backup-sql-server.md).  
  
### <a name="example-c-creating-a-compressed-backup-transact-sql"></a>Пример В. Создание сжатой резервной копии (Transact-SQL)  
 В следующем примере [BACKUP](/sql/t-sql/statements/backup-transact-sql) создается сжатая полная резервная копия базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] в чистом форматированном файле резервной копии `Z:\SQLServerBackups\AdvWorksData.bak`.  
  
```tsql  
--Run backup statement in the gBackup session.  
BACKUP DATABASE AdventureWorks2012 TO DISK='Z:\SQLServerBackups\AdvWorksData.bak'   
WITH   
   FORMAT,   
   MEDIADESCRIPTION='AdventureWorks2012 Compressed Data Backups'  
   DESCRIPTION='First database backup on AdventureWorks2012 Compressed Data Backups media set'  
   COMPRESSION;  
GO  
```  
  
 [&#91;В начало&#93;](#Top)  
  
## <a name="see-also"></a>См. также  
 [Создание и проверка определяемой пользователем функции-классификатора](../resource-governor/create-and-test-a-classifier-user-defined-function.md)   
 [Resource Governor](../resource-governor/resource-governor.md)  
  
  
