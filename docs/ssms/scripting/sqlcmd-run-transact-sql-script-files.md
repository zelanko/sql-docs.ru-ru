---
title: Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd
ms.custom: seo-lt-2019
ms.date: 07/15/2016
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ed85470d8e054ba60ae0b2525f773f83d70d0da3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253208"
---
# <a name="sqlcmd---run-transact-sql-script-files"></a>sqlcmd — выполнение файлов скрипта Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
  
