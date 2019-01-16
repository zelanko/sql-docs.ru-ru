---
title: Установка и настройка образца базы данных AdventureWorks — SQL | Документация Майкрософт
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a5eb1b2d0aa49b882afd9aa8b239a6bb64375563
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54299665"
---
# <a name="adventureworks-installation-and-configuration"></a>AdventureWorks установки и настройки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  > [!div class="nextstepaction"]
  > [Поделитесь своим мнением о SQL документация содержания!](https://aka.ms/sqldocsurvey)

Ссылки и инструкции по установке, загрузите AdventureWorks. 

## <a name="prerequisites"></a>предварительные требования

- [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) или [база данных Azure SQL](https://azure.microsoft.com/services/sql-database/). Для полной версии примера используйте SQL Server Evaluation, Developer или Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Для получения наилучших результатов используйте от июня 2016 г. или более поздней версии.
 
## <a name="github-links"></a>Ссылки на Github

- [Все файлы AdventureWorks для SQL Server 2014 2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Все файлы AdventureWorks для SQL 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Все файлы AdventureWorks для SQL 2008 и 2008 R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="oltp-downloads"></a>Загружает OLTP

Прямые ссылки на базы данных AdventureWorks OLTP версии можно найти ниже:

- [AdventureWorks2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Файлы для загрузки хранилища данных

Прямые ссылки на версии хранилища данных AdventureWorks можно найти ниже:

- [AdventureWorksDW2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008-dw.bak)

## <a name="creation-scripts"></a>Скрипты создания
Ниже сценарии могут использоваться для создания всей базы данных AdventureWorks, независимо от версии. 

- [Zip сценарии оперативной обработки Транзакций AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [База данных AdventureWorks DW сценарии Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="install-to-sql-server"></a>Установка для SQL Server

### <a name="restore-backup"></a>Восстановление резервной копии
Выполните следующие действия, чтобы восстановить резервную копию базы данных с помощью SQL Server Management Studio. 

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши **баз данных** узел и выберите **Restore Database**.
3. Выберите **устройства** и нажмите кнопку с многоточием (**...** )
4. В диалоговом окне **Выбор устройства резервного копирования**, нажмите кнопку **добавить**, перейдите к резервной копии базы данных в файловой системе сервера и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости изменить целевое расположение для данных и файлов журналов в **файлы** области. Обратите внимание на то, что это лучший способ размещения данных и файлы журнала на разных дисках.
6. Нажмите кнопку **ОК**. Это инициирует восстановление базы данных. После ее завершения вы получите базы данных AdventureWorks, установленных на экземпляре SQL Server.

Дополнительные сведения о восстановлении базы данных SQL Server, см. в разделе [восстановление резервной копии базы данных с помощью среды SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Присоединение файла данных
Выполните следующие действия, чтобы присоединить файл данных для базы данных с помощью SQL Server Management Studio.

1. Откройте SQL Server Management Studio и подключитесь к целевому экземпляру SQL Server.
2. Щелкните правой кнопкой мыши **баз данных** узел и выберите **Attach**.
3. Выберите **добавить** и перейдите к. MDF-файл, который вы хотите присоединить. 
1. Выберите файл и нажмите кнопку **ОК**. 
    1. Выбранная база данных должны отображаться в нижнем окне. Если в файл указан как «не найдено», щелкните многоточие (**...** ) рядом с именем файла и путь на правильный путь обновления. 
    1. При наличии только файла данных (MDF), а не файл журнала (LDF), а затем выделите .ldf в нижнем окне и выберите **удалить**. Это создаст новый файл журнала. 
1. Выберите **ОК** нужно вложить файл. После присоединения файла вы получите базы данных AdventureWorks, установленных на экземпляре SQL Server.  

Дополнительные сведения о добавлении файлов базы данных, см. в разделе [подключить базу данных](../relational-databases/databases/attach-a-database.md). 

## <a name="install-to-azure-sql-database"></a>Установить базу данных Azure SQL


Если у вас еще нет SQL Server в Azure, перейдите к [портала Azure](https://portal.azure.com/) и создать новую базу данных SQL. В создание базы данных, создании сервера. Следует обратить внимание сервера. См. в разделе [учебником](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) Создание базы данных за несколько минут.

1. Подключитесь к порталу Azure.
1. Выберите **создать ресурс** в левой верхней части панели навигации. 
1. Выберите **баз данных** , а затем выберите **базы данных SQL**. 
1. Введите требуемые сведения.
1. В **Выбор источника** выберите **пример (AdventureWorksLT)** для восстановления резервной копии последней резервной копии AdventureWorksLT.
1. Выберите **создать** для создания новой базы данных SQL, который является восстановленной копии базы данных AdventureWorksLT. 


## <a name="see-also"></a>См. также
[Учебники по SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[Учебники по ядру СУБД SQL Server](../relational-databases/database-engine-tutorials.md)
