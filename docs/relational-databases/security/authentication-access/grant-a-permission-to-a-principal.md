---
title: Предоставление разрешения для субъекта | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Grant permission to a principal
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e7dc2bff70e98420161d823207222c6c9205940
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043262"
---
# <a name="grant-a-permission-to-a-principal"></a>Предоставление разрешения для участника
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В данном разделе содержатся инструкции по предоставлению разрешения участнику [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Предоставление разрешения участнику с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Рассмотрим следующие рекомендации, которые упростят управление разрешениями.  
  
-   Предоставляйте разрешения ролям, а не отдельным именам входа или пользователям. Когда один пользователь заменяет другого, удалите уходящего пользователя из роли и добавьте в нее нового. Все разрешения, связанные с ролью, автоматически становятся доступными для нового пользователя. Если нескольким лицам в организации нужны одинаковые разрешения, то добавление их в одну роль предоставит им одинаковые разрешения.  
  
-   Поместите сходные защищаемые объекты (таблицы, представления и процедуры) в одну схему, а затем предоставьте этой схеме разрешения. Например, схема платежной ведомости может содержать несколько таблиц, представлений и хранимых процедур. Предоставляя доступ к схеме, можно сразу предоставить все разрешения, необходимые для осуществления расчетов. Дополнительные сведения о защищаемых объектах, которым можно предоставлять разрешения, см. в разделе [Securables](../../../relational-databases/security/securables.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Лицо, предоставляющее разрешение (или участник, указанный с аргументом AS), должны иметь либо само разрешение с аргументом GRANT OPTION, либо разрешение более высокого уровня, которое включает в себя предоставленное разрешение. Члены предопределенной роли сервера **sysadmin** могут предоставлять любые разрешения.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-grant-permission-to-a-principal"></a>Предоставление разрешения участнику  
  
1.  В обозревателе объектов разверните базу данных, содержащую объект, которому необходимо предоставить разрешение.  
  
    > [!NOTE]  
    >  Как правило, эти действия используются для предоставления разрешений хранимым процедурам, но их можно использовать и для добавления разрешений таблицам, представлениям, функциям, сборкам и другим защищаемым объектам. Дополнительные сведения см. в разделе [GRANT (Transact-SQL)](../../../t-sql/statements/grant-transact-sql.md).  
  
2.  Разверните папку **Программирование** .  
  
3.  Разверните папку **Хранимые процедуры** .  
  
4.  Щелкните правой кнопкой мыши хранимую процедуру и выберите **Свойства**.  
  
5.  В разделе выбора страницы диалогового окна **Свойства хранимой процедуры —** _имя\_хранимой\_процедуры_ щелкните **Разрешения**. Данная страница используется для добавления пользователей или ролей к хранимым процедурам и для назначения разрешений этим пользователям и ролям.  
  
6.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-grant-permission-to-a-principal"></a>Предоставление разрешения участнику  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 Дополнительные сведения см. в статьях [GRANT (Transact-SQL)](../../../t-sql/statements/grant-transact-sql.md) и [Разрешения объекта GRANT (Transact-SQL)](../../../t-sql/statements/grant-object-permissions-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Участники (компонент Database Engine)](../../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
