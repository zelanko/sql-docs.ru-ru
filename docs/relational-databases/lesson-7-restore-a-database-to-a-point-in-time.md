---
title: Занятие 7. Восстановление базы данных на момент времени | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: a9f99670-e1de-441e-972c-69faffcac17a
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3659e3be185c6148b7688a070fa162a877e56692
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32947159"
---
# <a name="lesson-7-restore-a-database-to-a-point-in-time"></a>Занятие 7. Восстановление базы данных на момент времени
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
На этом занятии вы восстановите базу данных AdventureWorks2014 на определенный момент времени между двумя резервными копиями журнала транзакций.  
  
Чтобы выполнить восстановление на определенный момент времени из традиционных резервных копий, потребуется полная резервная копия базы данных, возможно, разностная резервная копия и все файлы журналов транзакций вплоть до того момента, на который необходимо выполнить восстановление, и сразу после него. При использовании резервных копий моментальных снимков файлов требуются только два ближайших файла резервных копий журнала, которые ограничивают период восстановления. Требуются только два резервных набора моментальных снимков файлов, так как каждая операция резервного копирования журнала создает моментальный снимок каждого файла базы данных (то есть файла данных и файла журнала).  
  
Чтобы восстановить базу данных на определенный момент времени из резервных наборов моментальных снимков файлов, выполните указанные ниже действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  Откройте новое окно запроса и подключитесь к экземпляру SQL Server 2016 ядра СУБД в виртуальной машине Azure.  
  
3.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окно запроса, а затем выполните его. Убедитесь в том, что таблица Production.Location содержит 29 939 строк, прежде чем восстанавливать ее на момент времени, когда было меньше строк, в шаге 5.  
  
    ```  
  
    -- Verify row count at start  
    SELECT COUNT (*) from AdventureWorks2014.Production.Location  
  
    ```  
  
    ![Отображается 29 939 строк](../relational-databases/media/5e2f4229-1970-49c9-89b3-e96b6f7fde83.JPG "Отображается 29 939 строк")  
  
4.  Скопируйте и вставьте приведенный ниже скрипт Transact-SQL в окне запроса. Выберите два смежных файла резервных копий журнала и укажите вместо их имен дату и время, требуемые для этого скрипта. Измените URL-адрес в соответствии с именем учетной записи хранения и контейнером, которые были указаны на занятии 1, укажите имена первого и второго файлов резервных копий, укажите время STOPAT в формате "26 июня, 2015 13:48", а затем выполните этот скрипт. Выполнение скрипта займет несколько минут.  
  
    ```  
  
    -- restore and recover to a point in time between the times of two transaction log backups, and then verify the row count  
    ALTER DATABASE AdventureWorks2014 SET SINGLE_USER WITH ROLLBACK IMMEDIATE;  
    RESTORE DATABASE AdventureWorks2014   
       FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/<firstbackupfile>.bak'   
       WITH NORECOVERY,REPLACE;  
    RESTORE LOG AdventureWorks2014   
       FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/<secondbackupfile>.bak'    
       WITH RECOVERY, STOPAT = 'June 26, 2015 01:48 PM';  
    ALTER DATABASE AdventureWorks2014 set multi_user;  
    -- get new count  
    SELECT COUNT (*) FROM AdventureWorks2014.Production.Location ;  
  
    ```  
  
5.  Просмотрите выходные данные. Обратите внимание на то, что после восстановления число строк равно 18 389 — это число строк межу резервными копиями журнала 5 и 6 (ваше число строк может быть другим).  
  
    ![Область результатов отображает число строк после восстановления до точки во времени](../relational-databases/media/4a0c6d8b-e2ed-4e93-bd7a-ade22a4aecc6.JPG "Область результатов отображает число строк после восстановления до точки во времени")  
  
**Следующее занятие:**  
  
[Занятие 8. Восстановление в качестве новой базы данных из резервной копии журнала](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)  
  
  
  
