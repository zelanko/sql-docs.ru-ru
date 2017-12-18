---
title: "Устройство резервного копирования (страница \"Общие\") | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: backup-restore
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.backupdevice.general.f1
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b7aff7cfef8a57056964cc688c563edce84cbe92
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="backup-device-general-page"></a>Устройство резервного копирования (страница «Общие»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] На странице **Общие** можно указать или просмотреть общие свойства логического устройства резервного копирования.  
  
 **Использование среды SQL Server Management Studio для просмотра содержимого устройства резервного копирования**  
  
-   [Просмотр содержимого ленты или файла резервной копии (SQL Server)](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Параметры  
 **Имя устройства**  
 Просмотр имени существующего логического устройства резервного копирования или создание нового имени логического устройства резервного копирования.  
  
 **Лента**  
 Просмотр и выбор целевого ленточного устройства из списка **Лента** . Этот параметр доступен, только если к компьютеру, на котором выполняется экземпляр компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], подключен ленточный накопитель.  
  
> [!NOTE]  
>  Устройства резервного копирования на магнитных лентах на удаленных компьютерах не могут указываться в качестве места назначения резервной копии.  
  
 **Файл**  
 Просмотр целевого файла существующего логического устройства резервного копирования или указание целевого файла для нового логического устройства резервного копирования.  
  
-   Для существующего логического устройства резервного копирования отображается путь к файлу резервной копии. Поле **Файл** недоступно для редактирования, кнопка «Обзор» также недоступна.  
  
-   Для нового логического устройства резервного копирования необходимо указать путь файла резервной копии, для которого определяется логическое устройство резервного копирования. Это должен быть новый файл.  
  
     Для указания локального файла резервной копии нужно нажать кнопку «Обзор» справа от текстового поля **Файл** . Затем в диалоговом окне **Расположение файлов базы данных** перейдите к любому местоположению на любом из фиксированных дисков компьютера, на котором выполняется экземпляр сервера. Если файл резервной копии еще не существует, нужно ввести имя файла в поле **Имя файла** данного диалогового окна.  
  
     Или можно отредактировать поле **Файл** вручную, чтобы изменить путь, имя файла и расширение, указанные по умолчанию. Для указания удаленного файла в качестве места расположения резервной копии введите полное имя файла в формате UNC. Дополнительные сведения см. в разделе [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md), подключен ленточный накопитель.  
  
    > [!IMPORTANT]  
    >  Возможны сетевые ошибки в случае резервного копирования данных по сети, поэтому по его окончании рекомендуется сделать проверку. Дополнительные сведения см. в разделе [RESTORE VERIFYONLY (Transact-SQL)](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md).  
  
## <a name="remarks"></a>Замечания  
 Резервные копии на наборе из одного или нескольких устройств резервного копирования образуют отдельный набор носителей. *Набор носителей* — это упорядоченная коллекция носителей резервных копий, лент или дисковых файлов, на которые производили запись одна или несколько операций резервного копирования, получая доступ по фиксированному типу и номеру устройства. Сведения о наборах носителей см. в разделе [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md), подключен ленточный накопитель.  
  
 Инициализация физического устройства резервного копирования, соответствующего логическому устройству, производится при записи первой резервной копии в наборе носителей на логическое устройство резервной копии. Если физическое устройство резервного копирования представляет собой не существующий до этого момента файл, он создается на данном этапе.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Определение логического устройства резервного копирования для дискового файла (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [Указание в качестве назначения резервного копирования диска или ленты (SQL Server)](../../relational-databases/backup-restore/specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [Удаление устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)  
  
-   [Назначение срока хранения резервной копии (SQL Server)](../../relational-databases/backup-restore/set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [Просмотр содержимого ленты или файла резервной копии (SQL Server)](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Просмотр файлов данных и журналов в резервном наборе данных (SQL Server)](../../relational-databases/backup-restore/view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [Восстановление резервной копии с устройства (SQL Server)](../../relational-databases/backup-restore/restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Наборы носителей, семейства носителей и резервные наборы данных (SQL Server)](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
