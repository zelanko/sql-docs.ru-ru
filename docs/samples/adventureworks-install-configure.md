---
title: Установка и Настройка образца базы данных AdventureWorks
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 6a4b56a31ede0d8e011c1a2244f5d014e185e7e5
ms.sourcegitcommit: 9e026cfd9f2300f106af929d88a9b43301f5edc2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74318998"
---
# <a name="adventureworks-installation-and-configuration"></a>Установка и настройка AdventureWorks
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Ссылки для загрузки AdventureWorks и инструкции по установке. 

## <a name="prerequisites"></a>Необходимые компоненты

- [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) или [база данных SQL Azure](https://azure.microsoft.com/services/sql-database/). Для полной версии примера используйте SQL Server Evaluation, Developer или Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Для получения наилучших результатов используйте выпуск Июнь 2016 или более поздней версии.
 
## <a name="oltp-downloads"></a>Загрузки OLTP

Прямые ссылки на версии OLTP AdventureWorks можно найти ниже:

- [AdventureWorks2017. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Загрузка хранилища данных

Прямые ссылки на версии AdventureWorks для хранилища данных можно найти ниже:

- [AdventureWorksDW2017. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008-dw.bak)

## <a name="creation-scripts"></a>Скрипты создания
Приведенные ниже скрипты можно использовать для создания всей базы данных AdventureWorks независимо от версии. 

- [ZIP-файл скриптов OLTP](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [ZIP-скрипты сценариев AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="github-links"></a>Ссылки GitHub

- [Все файлы AdventureWorks для SQL 2014-2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Все файлы AdventureWorks для SQL 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Все файлы AdventureWorks для SQL 2008 и 2008R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="install-to-sql-server"></a>Установка в SQL Server

### <a name="restore-backup"></a>Восстановить резервную копию
Выполните следующие действия, чтобы восстановить резервную копию базы данных с помощью SQL Server Management Studio. 

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши узел **базы данных** и выберите команду **восстановить базу данных**.
3. Выберите **устройство** и нажмите кнопку с многоточием (**...**).
4. В диалоговом окне **выберите устройства резервного копирования**, нажмите кнопку **Добавить**, перейдите к резервной копии базы данных в файловой системе сервера и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости измените целевое расположение файлов данных и журналов в области **файлы** . Обратите внимание, что рекомендуется размещать файлы данных и журналов на разных дисках.
6. Нажмите кнопку **ОК**. Это приведет к запуску восстановления базы данных. После завершения работы на экземпляре SQL Server будет установлена база данных AdventureWorks.

Дополнительные сведения о восстановлении базы данных SQL Server см. в разделе [Восстановление резервной копии базы данных с помощью SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Присоединение файла.
Выполните приведенные ниже действия, чтобы присоединить файл данных для вашей базы для работы с помощью SQL Server Management Studio.

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши узел **базы данных** и выберите команду **присоединить**.
3. Выберите **Добавить** и перейдите к. MDF файл, который нужно присоединить. 
1. Выберите файл и нажмите кнопку **ОК**. 
    1. Выбранная база данных должна отображаться в нижнем окне. Если файл указан как "не найден", нажмите кнопку с многоточием (**...**) рядом с именем файла и измените путь на правильный путь. 
    1. Если у вас есть только файл данных (MDF), а не файл журнала (LDF), выделите расширение LDF в нижнем окне и выберите **Удалить**. Будет создан новый файл журнала. 
1. Нажмите кнопку **ОК** , чтобы присоединить файл. После присоединения файла на вашем экземпляре SQL Server будет установлена база данных AdventureWorks.  

Дополнительные сведения о присоединении файлов базы данных см. в разделе [Присоединение базы данных](../relational-databases/databases/attach-a-database.md). 

## <a name="install-to-azure-sql-database"></a>Установка в базу данных SQL Azure


Если у вас еще нет SQL Server в Azure, перейдите к [портал Azure](https://portal.azure.com/) и создайте новую базу данных SQL. В процессе создания базы данных будет создан сервер. Запишите сервер. Ознакомьтесь с [этим руководством](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) , чтобы создать базу данных за считаные минуты.

1. Подключитесь к портал Azure.
1. Выберите **создать ресурс** в верхнем левом углу панели навигации. 
1. Выберите **Базы данных** и **База данных SQL**. 
1. Введите запрошенные сведения.
1. В поле **Select Source (Выбор источника** **) выберите Sample (AdventureWorksLT)** , чтобы восстановить резервную копию последней резервной копии AdventureWorksLT.
1. Выберите **создать** , чтобы создать новую базу данных SQL, которая является восстановленной копией базы данных AdventureWorksLT. 


## <a name="see-also"></a>См. также:
[Руководства для SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[Учебники по SQL Server ядру СУБД](../relational-databases/database-engine-tutorials.md)
