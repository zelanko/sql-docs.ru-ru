---
title: Создание спецификации аудита для сервера и базы данных
description: Узнайте, как создать спецификацию аудита SQL Server и базы данных с помощью SQL Server Management Studio или Transact-SQL (T-SQL).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.sqlaudit.dbaudit.general.f1
helpviewer_keywords:
- audits [SQL Server], creating database specification
- database audit [SQL Server]
ms.assetid: 26ee85de-6e97-4318-b526-900924d96e62
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 55b848cd43e157a9a75670a24aea645c3279f7ea
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82262073"
---
# <a name="create-a-server-audit-and-database-audit-specification"></a>Создание спецификации аудита для сервера и базы данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этой статье описано, как создать аудит сервера и спецификацию аудита базы данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Аудит экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включает в себя отслеживание и протоколирование событий, происходящих в системе. Объект *подсистема аудита SQL Server* объединяет отдельные экземпляры действий или групп действий уровня сервера или базы данных, за которыми нужно проводить наблюдение. Аудит работает на уровне экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . На одном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может существовать несколько аудитов. Объект *Спецификация аудита на уровне базы данных* также принадлежит подсистеме аудита. Для аудита вы можете создать одну спецификацию аудита базы данных для каждой базы данных SQL Server. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (ядро СУБД)](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 Спецификации аудита базы данных являются незащищаемыми объектами, которые находятся в определенной базе данных. После создания спецификация аудита базы данных находится в отключенном состоянии.  
  
 Если спецификация аудита базы данных создается или изменяется в пользовательской базе данных, не включайте действия аудита для объектов области сервера, таких как системные представления. Если вы включаете объекты области сервера, аудит будет создан, но объекты области сервера не будут включены и при этом не будет возвращаться ошибка. Для аудита объектов области сервера используйте спецификацию аудита базы данных в базе данных master.  
  
 Спецификации аудита базы данных размещаются в базе данных, где они были созданы, за исключением системной базы данных **TempDB**.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
  
-   Пользователи с разрешением ALTER ANY DATABASE AUDIT могут создавать спецификации аудита базы данных и привязывать их к любому аудиту.  
  
-   После создания спецификации аудита базы данных ее могут просматривать субъекты с разрешениями CONTROL SERVER или ALTER ANY DATABASE AUDIT, а также учетная запись sysadmin.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-server-audit"></a>Создание аудита сервера  
  
1.  В обозревателе объектов раскройте папку **Безопасность** .  
  
2.  Щелкните правой кнопкой мыши папку **Аудиты** и выберите пункт **Создать аудит**. Дополнительные сведения см. в статье [Создание аудита сервера и спецификации аудита сервера](../../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md).  
  
3.  Выбрав параметры, нажмите **ОК**.  

#### <a name="to-create-a-database-level-audit-specification"></a>Создание спецификации аудита на уровне базы данных  
  
1.  В обозревателе объектов разверните базу данных, в которой необходимо создать спецификацию аудита.  
  
2.  Разверните папку **Безопасность** .  
  
3.  Щелкните правой кнопкой мыши папку **Спецификации аудита базы данных** и выберите пункт **Создать спецификацию аудита базы данных**.  
  
     В диалоговом окне **Создание спецификации аудита базы данных** доступны следующие параметры:  
  
     **имя**;  
     Имя спецификации аудита базы данных. Имя формируется автоматически во время создания новой спецификации аудита сервера. Имя можно изменять.  
  
     **Аудит**  
     Имя существующего объекта аудита сервера. Введите имя аудита или выберите его из списка.  
  
     **Тип действия аудита**  
     Указывает группы действий аудита на уровне базы данных и действия аудита для захвата. Список групп действий аудита на уровне базы данных, действия аудита и описание содержащихся в них событий см. в статье [Действия и группы действий подсистемы аудита SQL Server](../../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
     **Схема объекта**  
     Отображает схему для указанного **Имени объекта**.  
  
     **Имени объекта**  
     Имя объекта для аудита. Этот параметр доступен только для действий аудита. Он не применяется к группам аудита.  
  
     **Кнопка с многоточием (...)**  
     Открывает диалоговое окно **Выбор объектов** для просмотра и выбора доступного объекта на основе указанного **Типа действия аудита**.  
  
     **Имя участника**  
     Учетная запись для фильтрации аудита для объекта, подвергнутого аудиту.  
  
     **Кнопка с многоточием (...)**  
     Открывает диалоговое окно **Выбор объектов** для просмотра и выбора доступного объекта на основе указанного значения **Имя объекта**.  
  
4.  Выбрав параметры, нажмите **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-server-audit"></a>Создание аудита сервера  
  
1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Вставьте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE master ;  
    GO  
    -- Create the server audit.   
    CREATE SERVER AUDIT Payrole_Security_Audit  
        TO FILE ( FILEPATH =   
    'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA' ) ;   
    GO  
    -- Enable the server audit.   
    ALTER SERVER AUDIT Payrole_Security_Audit   
    WITH (STATE = ON) ;  
    ```  
  
#### <a name="to-create-a-database-level-audit-specification"></a>Создание спецификации аудита на уровне базы данных  
  
1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Вставьте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается спецификация аудита базы данных с именем `Audit_Pay_Tables`. Выполняется аудит инструкций SELECT и INSERT от пользователя `dbo` для таблицы `HumanResources.EmployeePayHistory` на основе аудита сервера, определенного в предыдущем разделе.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    -- Create the database audit specification.   
    CREATE DATABASE AUDIT SPECIFICATION Audit_Pay_Tables  
    FOR SERVER AUDIT Payrole_Security_Audit  
    ADD (SELECT , INSERT  
         ON HumanResources.EmployeePayHistory BY dbo )   
    WITH (STATE = ON) ;   
    GO  
  
    ```  
  
 Дополнительные сведения см. в статьях [CREATE SERVER AUDIT (Transact-SQL)](../../../t-sql/statements/create-server-audit-transact-sql.md) и [CREATE DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../../t-sql/statements/create-database-audit-specification-transact-sql.md).  
  
  
