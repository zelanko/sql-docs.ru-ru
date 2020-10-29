---
title: Настройка хранилища — кэш обратной записи NVDIMM-N
description: Сведения о том, как настроить зеркальное дисковое пространство с зеркальным кэшем обратной записи NVDIMM-N в качестве виртуального устройства для хранения журнала транзакций SQL Server.
ms.custom: seo-dt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 861862fa-9900-4ec0-9494-9874ef52ce65
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 7f95a343074ce2fb9f7f54c3121b0db6beafe34d
ms.sourcegitcommit: 22e97435c8b692f7612c4a6d3fe9e9baeaecbb94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2020
ms.locfileid: "92679230"
---
# <a name="configuring-storage-spaces-with-a-nvdimm-n-write-back-cache"></a>Настройка дисковых пространств с помощью кэша обратной записи NVDIMM-N
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Windows Server 2016 поддерживает устройства NVDIMM-N, которые обеспечивают высочайшую скорость операций ввода-вывода. Одним из привлекательных способов применения таких устройств является организация кэша обратной записи для обеспечения низкой задержки при записи. В этом разделе описывается, как настроить зеркальное дисковое пространство с зеркальным кэшем обратной записи NVDIMM-N в качестве виртуального устройства для хранения журнала транзакций SQL Server. Если вы также хотите использовать его для хранения таблиц или иных данных, вы можете добавить в пул носителей больше дисков или создать несколько пулов для обеспечения изоляции.  
  
 Чтобы просмотреть видео, посвященное использованию этой технологии, на канале Channel 9, перейдите на страницу [Использование энергонезависимой памяти (NVDIMM-N) в качестве блочного хранилища в Windows Server 2016](https://channel9.msdn.com/Events/Build/2016/P466).  
  
## <a name="identifying-the-right-disks"></a>Выбор подходящих дисков  
 Настраивать дисковые пространства в Windows Server 2016, особенно с расширенными функциями, такими как кэш обратной записи, проще всего с помощью PowerShell. Прежде всего следует определить, какие диски должны входить в пул дисковых пространств, на основе которого будет создаваться виртуальный диск. В устройствах NVDIMM-N применяется тип носителя и тип шины SCM, поддерживающий запросы посредством командлета PowerShell Get-PhysicalDisk.  
  
```  
Get-PhysicalDisk | Select FriendlyName, MediaType, BusType  
```  
  
 ![Снимок экрана окна Windows PowerShell с выходными данными командлета Get-PhysicalDisk.](../../relational-databases/performance/media/get-physicaldisk.png "Get-PhysicalDisk")  
  
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
  
 ![Снимок экрана окна Windows PowerShell с выходными данными командлета $pd.](../../relational-databases/performance/media/select-friendlyname.png "Select FriendlyName")  
  
## <a name="creating-the-storage-pool"></a>Создание пула носителей  
 Используя переменную $pd, содержащую физические диски, можно легко создать пул носителей с помощью командлета PowerShell New-StoragePool.  
  
```  
New-StoragePool -StorageSubSystemFriendlyName "Windows Storage*" -FriendlyName NVDIMM_Pool -PhysicalDisks $pd  
```  
  
 ![Снимок экрана окна Windows PowerShell с выходными данными командлета New-StoragePool.](../../relational-databases/performance/media/new-storagepool.png "New-StoragePool")  
  
## <a name="creating-the-virtual-disk-and-volume"></a>Создание виртуального диска и тома  
 После создания пула следует выделить виртуальный диск и отформатировать его. В этом случае будет создан только один виртуальный диск, и процесс можно упростить с помощью командлета PowerShell New-Volume.  
  
```  
New-Volume -StoragePool (Get-StoragePool -FriendlyName NVDIMM_Pool) -FriendlyName Log_Space -Size 300GB -FileSystem NTFS -AccessPath S: -ResiliencySettingName Mirror  
```  
  
 ![Снимок экрана окна Windows PowerShell с выходными данными командлета New-Volume.](../../relational-databases/performance/media/new-volume.png "New-Volume")  
  
 Виртуальный диск создан, инициализирован и отформатирован как NTFS. На снимке экрана ниже показано, что он имеет размер 300 ГБ и кэш обратной записи размером 1 ГБ, который будет размещаться на устройствах NVDIMM-N.  
  
 ![Снимок экрана окна Windows PowerShell с выходными данными командлета Get-VirtualDisk.](../../relational-databases/performance/media/get-virtualdisk.png "Get-VirtualDisk")  
  
 Теперь этот новый том можно увидеть на сервере. Этот диск можно использовать для хранения журнала транзакций SQL Server.  
  
 ![Снимок экрана окна проводника со страницей "Этот компьютер", где отображается диск Log_Space.](../../relational-databases/performance/media/log-space-drive.png "Log_Space Drive")  
  
## <a name="see-also"></a>См. также:  
 [Дисковые пространства Windows в Windows 10](https://windows.microsoft.com/windows-10/storage-spaces-windows-10)   
 [Дисковые пространства Windows в Windows 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831739(v=ws.11))   
 [Журнал транзакций (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [Просмотр или изменение расположения по умолчанию для файлов данных и журнала (среда SQL Server Management Studio)](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md)  
  
