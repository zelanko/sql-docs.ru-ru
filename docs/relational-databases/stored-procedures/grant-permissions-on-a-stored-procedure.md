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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6cac03be8a275f3918d509f028c56feaaa8b0518
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67580521"
---
# <a name="grant-permissions-on-a-stored-procedure"></a>Предоставление разрешений на хранимую процедуру
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В этом разделе описывается, как предоставить разрешения на хранимую процедуру в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , используя среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Разрешения можно предоставить существующему пользователю, роли базы данных или роли приложения в базе данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для предоставления разрешений на хранимую процедуру используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Нельзя использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для предоставления разрешений на системные процедуры или системные функции. Вместо этого используйте [Разрешения объекта GRANT](../../t-sql/statements/grant-object-permissions-transact-sql.md) .  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Объект, предоставляющий разрешение (или участник, указанный параметром AS), должен иметь либо само разрешение, выданное с помощью параметра GRANT OPTION, либо разрешение более высокого уровня, которое неявно включает предоставляемое. Необходимо разрешение ALTER на схему, которой принадлежит процедура, или разрешение CONTROL на процедуру. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на объект (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>Предоставление разрешений на хранимую процедуру  
  
1.  В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] и разверните его.  
  
2.  Последовательно разверните узел **Базы данных**, базу данных, которой принадлежит процедура, и узел **Программирование**.  
  
3.  Разверните узел **Хранимые процедуры**, щелкните правой кнопкой мыши процедуру для предоставления разрешений и выберите **Свойства**.  
  
4.  В пункте **Свойства хранимой процедуры**выберите страницу **Разрешения** .  
  
5.  Для предоставления разрешений пользователю, роли базы данных или роли приложения нажмите кнопку **Поиск**.  
  
6.  В пункте **Выбрать пользователей или ролей**нажмите **Типы объектов** для необходимого добавления или исключения пользователей и ролей.  
  
7.  Нажмите кнопку **Обзор** , чтобы показать список пользователей или ролей. Выберите пользователей или роли, которым следует предоставить разрешения.  
  
8.  В сетке **Явно указанные разрешения** выберите разрешения для предоставления определенному пользователю или роли. Описание разрешений см. в разделе [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md).  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 Выбор **Предоставить** означает, что получателю разрешения предоставляется указанное разрешение. Выбор параметра **Право передачи** означает, что получатель разрешения имеет возможность предоставить указанное разрешение другим участникам.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
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
  
  
