---
title: Настройка дисковых пространств с помощью кэша обратной записи NVDIMM-N | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 861862fa-9900-4ec0-9494-9874ef52ce65
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5c82af7b6d4daee215f0e532fc35666bf9cba42f
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="configuring-storage-spaces-with-a-nvdimm-n-write-back-cache"></a>Настройка дисковых пространств с помощью кэша обратной записи NVDIMM-N
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Windows Server 2016 поддерживает устройства NVDIMM-N, которые обеспечивают высочайшую скорость операций ввода-вывода. Одним из привлекательных способов применения таких устройств является организация кэша обратной записи для обеспечения низкой задержки при записи. В этом разделе описывается, как настроить зеркальное дисковое пространство с зеркальным кэшем обратной записи NVDIMM-N в качестве виртуального устройства для хранения журнала транзакций SQL Server. Если вы также хотите использовать его для хранения таблиц или иных данных, вы можете добавить в пул носителей больше дисков или создать несколько пулов для обеспечения изоляции.  
  
 Чтобы просмотреть видео, посвященное использованию этой технологии, на канале Channel 9, перейдите на страницу [Использование энергонезависимой памяти (NVDIMM-N) в качестве блочного хранилища в Windows Server 2016](https://channel9.msdn.com/Events/Build/2016/P466).  
  
## <a name="identifying-the-right-disks"></a>Выбор подходящих дисков  
 Настраивать дисковые пространства в Windows Server 2016, особенно с расширенными функциями, такими как кэш обратной записи, проще всего с помощью PowerShell. Прежде всего следует определить, какие диски должны входить в пул дисковых пространств, на основе которого будет создаваться виртуальный диск. В устройствах NVDIMM-N применяется тип носителя и тип шины SCM, поддерживающий запросы посредством командлета PowerShell Get-PhysicalDisk.  
  
```  
Get-PhysicalDisk | Select FriendlyName, MediaType, BusType  
```  
  
 ![Get-PhysicalDisk](../../relational-databases/performance/media/get-physicaldisk.png "Get-PhysicalDisk")  
  
> [!NOTE]  
>  При использовании устройств NVDIMM-N больше не требуется выбирать целевые устройства для кэша обратной записи.  
  
 Для создания зеркального виртуального диска с зеркальным кэшем обратной записи требуется по крайней мере 2 устройства NVDIMM-N и еще 2 других диска. Присвоение нужных физических дисков переменной перед созданием пула позволяет упростить процесс.  
  
```  
$pd =  Get-PhysicalDisk | Select FriendlyName, MediaType, BusType | WHere-Object {$_.FriendlyName -like 'MK0*' -or $_.FriendlyName -like '2c80*'}  
```  
  
 На снимке экрана показана переменная $pd, а также присвоенные ей 2 диска SSD и 2 устройства NVDIMM-N, возвращенные с помощью следующего командлета PowerShell.  
  
```  
$pd | Select FriendlyName, MediaType, BusType  
```  
  
 ![Выберите удобное имя](../../relational-databases/performance/media/select-friendlyname.png "Выберите удобное имя")  
  
## <a name="creating-the-storage-pool"></a>Создание пула носителей  
 Используя переменную $pd, содержащую физические диски, можно легко создать пул носителей с помощью командлета PowerShell New-StoragePool.  
  
```  
New-StoragePool –StorageSubSystemFriendlyName “Windows Storage*” –FriendlyName NVDIMM_Pool –PhysicalDisks $pd  
```  
  
 ![New-StoragePool](../../relational-databases/performance/media/new-storagepool.png "New-StoragePool")  
  
## <a name="creating-the-virtual-disk-and-volume"></a>Создание виртуального диска и тома  
 После создания пула следует выделить виртуальный диск и отформатировать его. В этом случае будет создан только один виртуальный диск, и процесс можно упростить с помощью командлета PowerShell New-Volume.  
  
```  
New-Volume –StoragePool (Get-StoragePool –FriendlyName NVDIMM_Pool) –FriendlyName Log_Space –Size 300GB –FileSystem NTFS –AccessPath S: -ResiliencySettingName Mirror  
```  
  
 ![New-Volume](../../relational-databases/performance/media/new-volume.png "New-Volume")  
  
 Виртуальный диск создан, инициализирован и отформатирован как NTFS. На снимке экрана ниже показано, что он имеет размер 300 ГБ и кэш обратной записи размером 1 ГБ, который будет размещаться на устройствах NVDIMM-N.  
  
 ![Get-VirtualDisk](../../relational-databases/performance/media/get-virtualdisk.png "Get-VirtualDisk")  
  
 Теперь этот новый том можно увидеть на сервере. Этот диск можно использовать для хранения журнала транзакций SQL Server.  
  
 ![Диск для хранения журнала](../../relational-databases/performance/media/log-space-drive.png "Диск для хранения журнала")  
  
## <a name="see-also"></a>См. также:  
 [Дисковые пространства Windows в Windows 10](http://windows.microsoft.com/en-us/windows-10/storage-spaces-windows-10)   
 [Дисковые пространства Windows в Windows 2012 R2](https://technet.microsoft.com/en-us/library/hh831739.aspx)   
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [Просмотр или изменение расположения по умолчанию для файлов данных и журнала (среда SQL Server Management Studio)](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md)  
  
  
