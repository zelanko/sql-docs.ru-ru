---
title: Предоставление разрешений на хранимую процедуру | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b76db9ab1e2380e6f7925ed0717f01ee2d053658
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000985"
---
# <a name="grant-permissions-on-a-stored-procedure"></a>Предоставление разрешений на хранимую процедуру
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  В этом разделе описывается, как предоставить разрешения на хранимую процедуру в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , используя среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Разрешения можно предоставить существующему пользователю, роли базы данных или роли приложения в базе данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для предоставления разрешений на хранимую процедуру используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Нельзя использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для предоставления разрешений на системные процедуры или системные функции. Вместо этого используйте [Разрешения объекта GRANT](../../t-sql/statements/grant-object-permissions-transact-sql.md) .  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое. Необходимо разрешение ALTER на схему, которой принадлежит процедура, или разрешение CONTROL на процедуру. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на объект (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>Предоставление разрешений на хранимую процедуру  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните узел **Хранимые процедуры**, щелкните правой кнопкой мыши процедуру для предоставления разрешений и выберите **Свойства**.  
  
4.  В пункте **Свойства хранимой процедуры**выберите страницу **Разрешения** .  
  
5.  Для предоставления разрешений пользователю, роли базы данных или роли приложения нажмите кнопку **Поиск**.  
  
6.  В пункте **Выбрать пользователей или ролей**нажмите **Типы объектов** для необходимого добавления или исключения пользователей и ролей.  
  
7.  Нажмите кнопку **Обзор** , чтобы показать список пользователей или ролей. Выберите пользователей или роли, которым следует предоставить разрешения.  
  
8.  В сетке **Явно указанные разрешения** выберите разрешения для предоставления определенному пользователю или роли. Описание разрешений см. в разделе [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md).  

 Выбор **Предоставить** означает, что получателю разрешения предоставляется указанное разрешение. Выбор параметра **Право передачи** означает, что получатель разрешения имеет возможность предоставить указанное разрешение другим участникам.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>Предоставление разрешений на хранимую процедуру  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере предоставляется разрешение `EXECUTE` на хранимую процедуру `HumanResources.uspUpdateEmployeeHireInfo` роли приложения с именем `Recruiting11`.  
  
```sql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [GRANT, предоставление разрешений на объект (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [Создание хранимой процедуры](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [Изменение хранимой процедуры](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [Удаление хранимой процедуры](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)   
 [Изменение имени хранимой процедуры](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)  
  
  
