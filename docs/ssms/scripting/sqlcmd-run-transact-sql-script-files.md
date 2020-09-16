---
title: Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd
description: Сведения о том, как использовать sqlcmd для запуска файла скрипта Transact-SQL. Он может содержать инструкции Transact-SQL, команды sqlcmd и переменные скриптов.
ms.custom: seo-lt-2019
ms.date: 07/15/2016
ms.prod: sql
ms.technology: ssms
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d842772e4ca65e4905d1e8134c4247a965ba46a
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88901246"
---
# <a name="sqlcmd---run-transact-sql-script-files"></a>sqlcmd — выполнение файлов скрипта Transact-SQL
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
 Для запуска файла скрипта Transact-SQL используйте **sqlcmd** . Файл скрипта Transact-SQL является текстовым файлом, содержащим сочетание инструкций Transact-SQL, команд **sqlcmd** и переменных скрипта.  

## <a name="create-a-script-file"></a>Создание файла скрипта  
 Чтобы создать простой файл скрипта Transact-SQL, используя приложение "Блокнот", следуйте перечисленным ниже шагам.  
  
1.  Нажмите кнопку **Пуск**, последовательно укажите пункты **Все программы**, **Стандартные**и выберите пункт **Блокнот**.  
  
2.  Скопируйте и вставьте следующий код языка Transact-SQL в приложение "Блокнот":  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  Сохраните файл под именем **myScript.sql** на диске C.  
  
## <a name="run-the-script-file"></a>Выполнение файла скрипта  
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите **sqlcmd -S myServer\instanceName -i C:\myScript.sql**  
  
3.  Нажмите клавишу ВВОД.  
  
 В окне командной строки будет выведен список имен и адресов сотрудников [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] .  

## <a name="save-the-output-to-a-text-file"></a>Сохранение результата в текстовом файле
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите **sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt**  
  
3.  Нажмите клавишу ВВОД.  
  
 Результат не будет выведен в окне командной строки. Он будет записан в файл EmpAdds.txt. Можно проверить полученные результаты, открыв файл EmpAdds.txt.  
  
## <a name="see-also"></a>См. также:  
 [Запуск программы sqlcmd](../../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
