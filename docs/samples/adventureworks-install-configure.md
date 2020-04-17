---
title: Установка и настройка выборочной базы данных AdventureWorks
description: Следуйте этим инструкциям для загрузки и установки выборочных баз данных AdventureWorks со студией управления серверами s'L или в базе данных Azure S'L.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 7fa3d199450750a444f2b67ae3e4583549d449b9
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484583"
---
# <a name="adventureworks-installation-and-configuration"></a>Установка и конфигурация AdventureWorks
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

AdventureWorks скачать ссылки и инструкции по установке. 

## <a name="prerequisites"></a>Предварительные требования

- [База данных Сервера или](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) [Лазурного Сервера](https://azure.microsoft.com/services/sql-database/). Для полной версии образца используйте s'L Server Evaluation/Developer/Enterprise Edition.
- [Студия управления серверами S'L](../ssms/download-sql-server-management-studio-ssms.md). Для достижения наилучших результатов используйте выпуск в июне 2016 года или позже.
 
## <a name="oltp-downloads"></a>ЗАГРУЗКа OLTP

Прямые ссылки на версии OLTP AdventureWorks можно найти ниже:

- [AdventureWorks2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Загрузка хранилища данных

Прямые ссылки на версии Хранилища данных AdventureWorks можно найти ниже:

- [AdventureWorksDW2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2.bak](https://github.com/microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-dw.bak)

## <a name="creation-scripts"></a>Сценарии создания
Ниже приведенные сценарии могут быть использованы для создания всей базы данных AdventureWorks, независимо от версии. 

- [AdventureWorks OLTP Скрипты Цип](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [AdventureWorks DW Скрипты Цип](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="github-links"></a>GitHub ссылки

- [Все файлы AdventureWorks для S'L 2014 - 2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Все файлы AdventureWorks для S'L 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Все файлы AdventureWorks для S'L 2008 и 2008R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="install-to-sql-server"></a>Установка на сервер S'L

### <a name="restore-backup"></a>Восстановление резервного копирования
Следуйте ниже шаги, чтобы восстановить резервную часть базы данных с помощью S'L Server Management Studio. 

1. Откройте студию управления серверами и подключитесь к целевому экземпляру S'L Server.
2. Нажмите на узла **базы данных** и выберите **базу данных восстановления.**
3. Выберите **устройство** и нажмите эллипсы **(...**)
4. В диалоге **Выберите резервные устройства,** нажмите **Добавить,** перейти к резервной системе базы данных в файловой системе сервера, и выберите резервную копию. Нажмите кнопку **ОК**.
5. При необходимости измените целевое местоположение для файлов данных и журналов в панели **файлов файлов.** Обратите внимание, что лучше всего размещать данные и журналировать файлы на разных дисках.
6. Нажмите кнопку **ОК**. Это инициирует восстановление базы данных. После завершения работы база данных AdventureWorks будет установлена на экземпляре сервера S'L.

Для получения дополнительной информации о восстановлении базы данных сервера S'L, [см. Восстановление резервной базы данных с помощью SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Прикрепите файл данных
Следуйте ниже шаги, чтобы прикрепить файл данных для базы данных с помощью S'L Server Management Studio.

1. Откройте студию управления серверами и подключитесь к целевому экземпляру S'L Server.
2. Нажмите на узла **базы данных** и выберите **Прикрепить.**
3. Выберите **Добавить** и перейти к . Файл MDF, который вы хотите прикрепить. 
1. Выберите файл и нажмите кнопку **ОК**. 
    1. Выбранная база данных должна отображаться в нижнем окне. Если файл указан как "не найден", выберите эллипсы **(...)** рядом с именем файла и обновите путь к правильному пути. 
    1. Если у вас есть только файл данных (.mdf), а не файл журнала (.ldf), затем выделите .ldf в нижнем окне и выберите **Удалить.** Это позволит создать новый файл журнала. 
1. Выберите **OK,** чтобы прикрепить файл. После присоединения файла база данных AdventureWorks будет установлена на экземпляре сервера S'L.  

Для получения дополнительной информации о присоединении файлов базы данных, [см.](../relational-databases/databases/attach-a-database.md) 

## <a name="install-to-azure-sql-database"></a>Установка в базу данных Azure S'L


Если у вас еще нет сервера S'L в Azure, перейдите на [портал Azure](https://portal.azure.com/) и создайте новую базу данных S'L. В процессе создания базы данных вы создадите сервер. Обратите внимание на сервер. Смотрите [этот учебник,](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) чтобы создать базу данных в считанные минуты.

1. Подключитесь к порталу Azure.
1. Выберите **Создать ресурс** в левом верхнем верхнем от навигационном стекол. 
1. Выберите **Базы данных** и **База данных SQL**. 
1. Заполните запрашиваемую информацию.
1. В поле **Select Source** выберите **образец (AdventureWorksLT)** для восстановления резервного копирования последней резервной копирования AdventureWorksLT.
1. Выберите **Создать** для создания новой базы данных S'L, которая является восстановленной копией базы данных AdventureWorksLT. 


## <a name="see-also"></a>См. также
[Учебники для студии управления серверами S'L](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[Учебники для движка базы данных S'L Server](../relational-databases/database-engine-tutorials.md)
