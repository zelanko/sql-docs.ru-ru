---
title: "Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "скрипты Transact-SQL"
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 42
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd
 Для запуска файла скрипта Transact-SQL используйте **sqlcmd**. Файл скрипта Transact-SQL является текстовым файлом, содержащим сочетание инструкций Transact-SQL, команд **sqlcmd** и переменных скрипта.  

## Создание файла скрипта  
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
  
## Выполнение файла скрипта  
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите **sqlcmd -S myServer\instanceName -i C:\myScript.sql**  
  
3.  Нажмите клавишу ВВОД.  
  
 В окне командной строки будет выведен список имен и адресов сотрудников [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)].  

## Сохранение результата в текстовом файле
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите **sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt**  
  
3.  Нажмите клавишу ВВОД.  
  
 Результат не будет выведен в окне командной строки. Он будет записан в файл EmpAdds.txt. Можно проверить полученные результаты, открыв файл EmpAdds.txt.  
  
## См. также:  
 [Запуск программу sqlcmd](../../relational-databases/scripting/start-the-sqlcmd-utility.md)   
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)  
  
  