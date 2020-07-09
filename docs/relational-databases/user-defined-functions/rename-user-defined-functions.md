---
title: Переименование определяемых пользователем функций | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c80d1d948f24c212c547c9367f05802c8570fe01
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768310"
---
# <a name="rename-user-defined-functions"></a>Переименование определяемых пользователем функций
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Определяемые пользователем функции в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно переименовать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для переименования определяемой пользователем функции используются.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Имена функций должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
-   При переименовании определяемой пользователем функции не изменяется имя соответствующего объекта в столбце определения представления каталога **sys.sql_modules** . Поэтому не рекомендуется переименовывать объекты этого типа. Лучше удалить хранимую процедуру и создать ее повторно с новым именем.  
  
-   Изменение имени или определения определяемой пользователем функции может привести к тому, что все зависящие от нее объекты при выполнении будут возвращать ошибку, если они не будут обновлены в соответствии с внесенными в функцию изменениями.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для удаления функции у пользователя должно быть разрешение ALTER на схему, которой принадлежит функция, или разрешение CONTROL на функцию. Для повторного создания функции требуется разрешение CREATE FUNCTION на базу данных и разрешение ALTER на схему, в которой создается функция.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-user-defined-functions"></a>Переименование определяемой пользователем функции  
  
1.  В **обозревателе объектов**щелкните значок «плюс» рядом с базой данных, содержащей функцию, которую нужно переименовать.  
  
2.  Щелкните значок «плюс» рядом с папкой **Программирование** .  
  
3.  Щелкните значок «плюс» рядом с папкой, содержащей функцию, которую надо переименовать.  
  
    -   Table-valued Function  
  
    -   Скалярная функция  
  
    -   Агрегатная функция  
  
4.  Щелкните правой кнопкой мыши функцию, которую нужно переименовать, и выберите пункт **Переименовать**.  
  
5.  Введите новое имя функции.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Переименование определяемой пользователем функции**  
  
 Эту задачу нельзя выполнить с помощью инструкций Transact-SQL. Чтобы переименовать определяемую пользователем функцию с помощью Transact-SQL, необходимо сначала удалить существующую функцию, а затем создать ее повторно с новым именем. Убедитесь, что весь код и приложения, ссылающиеся на старое имя функции, теперь используют новое имя.  
  
 Дополнительные сведения см. в разделах [CREATE FUNCTION (Transact-SQL)](../../t-sql/statements/create-function-transact-sql.md) и [DROP FUNCTION (Transact-SQL)](../../t-sql/statements/drop-function-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [Просмотр пользовательских функций](../../relational-databases/user-defined-functions/view-user-defined-functions.md)  
  
  
