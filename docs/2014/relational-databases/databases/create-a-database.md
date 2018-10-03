---
title: Создание базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], creating
- database creation [SQL Server], SQL Server Management Studio
- creating databases
ms.assetid: 4c4beea2-6cbc-4352-9db6-49ea8130bb64
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88367f2c01be6ba0cf6edaf2760d3f1e8f2c9482
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073234"
---
# <a name="create-a-database"></a>Создание базы данных
  В этом разделе описывается создание базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Создание базы данных с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]может быть задано не более 32 767 баз данных.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Инструкция CREATE DATABASE должна выполняться в режиме автоматической фиксации (режим управления транзакциями по умолчанию) и не может применяться в явной или неявной транзакции.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Резервную копию базы данных [master](master-database.md) необходимо создавать каждый раз при создании, изменении или удалении пользовательской базы данных.  
  
-   При создании базы данных файлы данных следует делать как можно большего размера, в соответствии с максимальным предполагаемым объемом данных в базе данных.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение CREATE DATABASE в базе данных master или разрешение CREATE ANY DATABASE или ALTER ANY DATABASE.  
  
 В целях сохранения управления над использованием диска в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]разрешение на создание баз данных обычно предоставляется небольшому числу учетных записей входа.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-database"></a>Создание базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Щелкните правой кнопкой мыши элемент **Базы данных**, а затем выберите пункт **Создать базу данных**.  
  
3.  В поле **Новая база данных**введите имя базы данных.  
  
4.  Чтобы создать базу данных, приняв все значения по умолчанию, нажмите кнопку **ОК**; иначе продолжайте выполнение следующих дополнительных шагов.  
  
5.  Чтобы изменить имя владельца, нажмите (**…**) и выберите другого владельца.  
  
    > [!NOTE]  
    >  Параметр **Использовать полнотекстовое индексирование** всегда установлен и недоступен (т. к. начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]все пользовательские базы данных поддерживают полнотекстовый поиск).  
  
6.  Чтобы изменить значения первичных данных по умолчанию и файлов журнала транзакций, щелкните соответствующую ячейку в сетке **Файлы базы данных** и введите новое значение. Дополнительные сведения см. в статье [AДобавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md).  
  
7.  Чтобы изменить параметры сортировки базы данных, выберите страницу **Параметры** и выберите из списка желаемые параметры сортировки.  
  
8.  Чтобы изменить модель восстановления, выберите страницу **Параметры** и модель восстановления из списка.  
  
9. Чтобы изменить параметры базы данных, выберите страницу **Параметры** и измените параметры базы данных. Описание каждого параметра см. в статье [Параметры ALTER DATABASE SET (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
10. Чтобы добавить новую файловую группу, перейдите на страницу **Группы файлов** . Нажмите **Добавить** и введите значения для файловой группы.  
  
11. Чтобы добавить расширенное свойство в базу данных, выберите страницу **Расширенные свойства** .  
  
    1.  В столбце **Имя** введите имя расширенного свойства.  
  
    2.  В столбце **Значение** введите текст расширенного свойства. Например, введите одно или несколько предложений, которые описывают базу данных.  
  
12. Чтобы создать базу данных, нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-create-a-database"></a>Создание базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается база данных `Sales`. Ключевое слово PRIMARY не использовано, поэтому первый файл (`Sales`_`dat`) становится первичным файлом. Поскольку в параметре SIZE для файла `Sales`\_`dat` не заданы суффиксы MB и KB, используется значение MB и пространство выделяется в мегабайтах. Резервную копию базы данных `Sales`\_`log` выделено в мегабайтах, потому что суффикс `MB` явно указан в параметре `SIZE` .  
  
```tsql  
USE master ;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
 Дополнительные примеры см. в статье [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Файлы и файловые группы базы данных](database-files-and-filegroups.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](database-detach-and-attach-sql-server.md)   
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [Добавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md)  
  
  
