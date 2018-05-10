---
title: Учебник. Использование службы хранилища больших двоичных объектов Azure с базами данных SQL Server 2016 | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c2aef9476c254267156c5bbde4d777a2ed5ab570
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="tutorial-use-azure-blob-storage-service-with-sql-server-2016"></a>Учебник. Использование службы хранилища больших двоичных объектов Azure с базами данных SQL Server 2016
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Добро пожаловать в учебник по работе с SQL Server 2016 в службе хранилища BLOB-объектов Microsoft Azure. С помощью этого учебника вы научитесь использовать службу хранилища BLOB-объектов Microsoft Azure для сохранения файлов данных и резервных копий SQL Server.  
  
Поддержка интеграции SQL Server со службой хранилища BLOB-объектов Microsoft Azure появилась в SQL Server 2012 с пакетом обновления 1 (SP1) и накопительным пакетом обновления  2 и в дальнейшем была улучшена в SQL Server 2014 и SQL Server 2016. Обзор функций и преимуществ использования этих функций см. в разделе [Файлы данных SQL Server в Microsoft Azure](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md). Работа функции показана в [видеоролике, посвященном восстановлению до точки во времени](https://channel9.msdn.com/Blogs/Windows-Azure/File-Snapshot-Backups-Demo).  
  
  
**Загрузить**<br /><br />**>>**  Чтобы скачать [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], перейдите на сайт  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.<br /><br />**>>**  Есть учетная запись Azure?  Тогда перейдите **[сюда](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/)** , чтобы запустить виртуальную машину с уже установленным [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .  
  
## <a name="what-you-will-learn"></a>Новые знания  
В этом учебнике в ходе ряда занятий показано, как работать с файлами данных SQL Server в службе хранилища BLOB-объектов Microsoft Azure. В каждом занятии рассматривается определенная задача, и занятия следует выполнять по порядку. Сначала вы узнаете, как создать контейнер в хранилище BLOB-объектов с помощью хранимой политики доступа и подписанного URL-адреса. Затем вы узнаете, как создать учетные данные SQL Server, чтобы интегрировать SQL Server с хранилищем BLOB-объектов Azure. Далее вы выполните резервное копирование базы данных в хранилище BLOB-объектов и восстановите ее в виртуальной машине Azure. После этого вы используете резервную копию журнала транзакций SQL Server 2016 на основе моментального снимка файла, чтобы выполнить восстановление в новой базе данных на определенный момент времени. Наконец, в учебнике будет продемонстрировано использование хранимых процедур и функций системы метаданных, что позволит вам понять, как работать с резервными копиями моментальных снимков файлов.  
  
В этом учебнике предполагается следующее:  
  
-   У вас есть локальный экземпляр SQL Server 2016 с установленной копией базы данных AdventureWorks2014.  
  
-   У вас есть учетная запись хранения Azure.  
  
-   У вас есть по крайней мере одна виртуальная машина Azure с SQL Server 2016, которая подготовлена в соответствии с инструкциями в статье [Подготовка виртуальной машины SQL Server на портале Azure](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-provision-sql-server/). Для выполнения сценария на [занятии 8 "Восстановление в качестве новой базы данных из резервной копии журнала"](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md) можно использовать вторую виртуальную машину.  
  
Этот учебник разделен на девять занятий, которые необходимо проходить по порядку.  
  
**[Занятие 1. Создание хранимой политики доступа и подписанного URL-адреса для контейнера Azure](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
На этом занятии вы создадите политику в новом контейнере BLOB-объектов, а также сформируете подписанный URL-адрес, который будет использоваться при создании учетных данных SQL Server.  
  
**[Занятие 2. Создание учетных данных SQL Server с помощью подписанного URL-адреса](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
На этом занятии вы создадите учетные данные с помощью ключа SAS для хранения сведений о безопасности, которые будут использоваться для доступа к учетной записи хранения Microsoft Azure.  
  
**[Занятие 3. Резервное копирование базы данных по URL-адресу](../relational-databases/lesson-3-database-backup-to-url.md)**  
На этом занятии вы выполните резервное копирование локальной базы данных в хранилище BLOB-объектов Microsoft Azure.  
  
**[Занятие 4. Восстановление базы данных в виртуальной машине с URL-адреса](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
На этом занятии вы восстановите базу данных в виртуальной машине Azure из хранилища BLOB-объектов Microsoft Azure.  
  
**[Занятие 5. Резервное копирование базы данных с помощью резервной копии моментального снимка](../relational-databases/lesson-5-backup-database-using-file-snapshot-backup.md)**  
На этом занятии вы создадите резервную копию базы данных посредством резервного копирования моментальных снимков файлов и просмотрите метаданные моментальных снимков файлов.  
  
**[Занятие 6. Создание журнала действий и резервного копирования с помощью резервного копирования моментальных снимков файлов](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
На этом занятии вы создадите действие в базе данных, создадите несколько резервных копий журнала посредством резервного копирования моментальных снимков файлов и просмотрите метаданные моментальных снимков файлов.  
  
**[Занятие 7. Восстановление базы данных на момент времени](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
На этом занятии вы восстановите базу данных на определенный момент времени с помощью двух резервных копий журнала на основе моментальных снимков файлов.  
  
**[Занятие 8. Восстановление в качестве новой базы данных из резервной копии журнала](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)**  
На этом занятии вы выполните восстановление из резервной копии журнала на основе моментального снимка файла в новой базе данных в другой виртуальной машине.  
  
**[Занятие 9. Управление резервными наборами данных и резервными копиями моментальных снимков файлов](../relational-databases/lesson-9-manage-backup-sets-and-file-snapshot-backups.md)**  
На этом занятии вы удалите ненужные резервные наборы и узнаете, как удалять потерянные резервные копии моментальных снимков файлов (когда это необходимо).  
  
## <a name="see-also"></a>См. также:  
[Файлы данных SQL Server в Microsoft Azure](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md)  
[Резервные копии моментальных снимков файлов для файлов базы данных в Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[Резервное копирование в SQL Server по URL-адресу](../relational-databases/backup-restore/sql-server-backup-to-url.md)  
  
  
  

