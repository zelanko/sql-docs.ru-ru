---
title: Создание схемы базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 10dd4ad8d0dcbd63e7133e2daf4d35a70695da19
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031571"
---
# <a name="create-a-database-schema"></a>Создание схемы базы данных
  В этом разделе описывается создание схемы в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Создание схемы с помощью следующих средств**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Новая схема принадлежит одному из следующих участников уровня базы данных: пользователю базы данных, роли базы данных или роли приложения. Объекты, создаваемые в схеме, принадлежат владельцу схемы и имеют значение NULL для **principal_id** в **sys.objects**. Владение объектами, содержащимися в схеме, можно передать любому участнику уровня базы данных, однако у владельца схемы всегда остается разрешение CONTROL на объекты в схеме.  
  
-   Если при создании объекта базы данных указать допустимого участника домена (пользователя или группу) в качестве владельца объекта, то этот участник будет добавлен в базу данных в качестве схемы. Новая схема будет принадлежать этому участнику домена.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
  
-   Требует разрешения CREATE SCHEMA в базе данных.  
  
-   Чтобы назначить другого пользователя владельцем создаваемой схемы, у участника должно быть разрешение IMPERSONATE на этого пользователя. Если роль базы данных указана в качестве владельца, то вызывающий объект должен входить в роль или иметь на нее разрешение ALTER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
##### <a name="to-create-a-schema"></a>Создание схемы  
  
1.  В обозревателе объектов раскройте папку **Базы данных** .  
  
2.  Разверните базу данных, в которой создается новая схема базы данных.  
  
3.  Щелкните правой кнопкой мыши папку **Безопасность** , укажите на пункт **Создать**и выберите **Схема**.  
  
4.  В диалоговом окне **Схема — создать** на странице **Общие** введите имя новой схемы в поле **Имя схемы** .  
  
5.  В поле **Владелец схемы** введите имя пользователя или роли базы данных, которые будут владельцем схемы. Также можно нажать кнопку **Поиск** , чтобы открыть диалоговое окно **Поиск ролей и пользователей** .  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>Дополнительные параметры  
 Диалоговое окно **Схема — Создать** также содержит параметры на двух дополнительных страницах: **Разрешения** и **Расширенные свойства**.  
  
-   На странице **Разрешения** перечислены все возможные защищаемые объекты и разрешения на эти объекты, которые могут быть предоставлены для имени входа.  
  
-   Страница **Расширенные свойства** позволяет добавлять пользовательские свойства пользователям базы данных.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-schema"></a>Создание схемы  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the schema Sprockets owned by Annik that contains table NineProngs.   
    -- The statement grants SELECT to Mandar and denies SELECT to Prasanna.  
  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [CREATE SCHEMA (Transact-SQL)](/sql/t-sql/statements/create-schema-transact-sql).  
  
  
