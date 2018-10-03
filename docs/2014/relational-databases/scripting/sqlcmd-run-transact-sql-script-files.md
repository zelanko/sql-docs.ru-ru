---
title: Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7dd52c6fb0c5533450a7e32ad68a156406873fdb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085376"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a>Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd
  Для запуска файла скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] можно использовать программу командной строки `sqlcmd`. Объект [!INCLUDE[tsql](../../includes/tsql-md.md)] файл скрипта — это текстовый файл, который может содержать сочетание [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций, `sqlcmd` команды и переменные скрипта.  
  
 Чтобы создать простой файл скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)], используя приложение «Блокнот», следуйте перечисленным ниже шагам.  
  
1.  Нажмите кнопку **Пуск**, последовательно укажите пункты **Все программы**, **Стандартные**и выберите пункт **Блокнот**.  
  
2.  Скопируйте и вставьте следующий [!INCLUDE[tsql](../../includes/tsql-md.md)] код в Блокнот:  
  
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
  
### <a name="to-run-the-script-file"></a>Выполнение файла скрипта  
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите следующую команду: `sqlcmd -S myServer\instanceName -i C:\myScript.sql`  
  
3.  Нажмите клавишу ВВОД.  
  
 В окне командной строки будет выведен список имен и адресов сотрудников [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] .  
  
### <a name="to-save-this-output-to-a-text-file"></a>Сохранение результата в текстовом файле  
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите следующую команду: `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`  
  
3.  Нажмите клавишу ВВОД.  
  
 Результат не будет выведен в окне командной строки. Он будет записан в файл EmpAdds.txt. Можно проверить полученные результаты, открыв файл EmpAdds.txt.  
  
## <a name="see-also"></a>См. также  
 [Запуск программу sqlcmd](sqlcmd-start-the-utility.md)   
 [Служебная программа sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
