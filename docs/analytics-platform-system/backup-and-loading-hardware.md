---
title: Резервное копирование и загрузка оборудованию для APS PDW
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: Для развертывания хранилища решения на Analytics Platform System (APS) с SQL Server Parallel данных хранилища (PDW) начала до конца данных, необходимо создать план резервного копирования в хранилище данных и загрузку данных.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 3a2ae046-f8d8-4a5c-b3c1-6ecee005df6c
caps.latest.revision: 9
ms.openlocfilehash: 8979b0d7b14f3e6b3de2834fdc800c5281d057ad
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="backup-and-loading-hardware-overview"></a>Резервное копирование и загрузка оборудованию
Для развертывания хранилища решения на Analytics Platform System (APS) с SQL Server Parallel данных хранилища (PDW) начала до конца данных, необходимо создать план резервного копирования в хранилище данных и загрузку данных. Используйте для получения и настройки резервного копирования и загрузку серверов, отвечающие требованиям организации.  
  
## <a name="acquire-and-configure-backup-servers"></a>Приобретать и настраивать резервных серверов  
![Процесс резервного копирования](media/backup-process.png "процесс резервного копирования")  
  
Для создания резервной копии базы данных PDW, требуется один или несколько серверов резервного копирования. Можно использовать существующие оборудования или приобретения нового оборудования. Дополнительные сведения см. в разделе [приобретать и настраивать резервное копирование сервера](acquire-and-configure-backup-server.md). Эти инструкции включают [резервное копирование журнала планирования емкости сервера](backup-capacity-planning-worksheet.md) при планировании подходящее решение для резервного копирования.  
  
## <a name="acquire-and-configure-loading-servers"></a>Приобретать и настраивать серверы загрузки  
![Процесс загрузки](media/loading-process.png "процесс загрузки")  
  
Чтобы загрузить данные, требуется один или несколько серверов загрузки. Можно использовать собственные существующих ETL или других серверах, или можно приобрести новые серверы. Дополнительные сведения см. в разделе [получения и настройки сервера загрузки](acquire-and-configure-loading-server.md). Эти инструкции включают [загрузки журнала планирования емкости сервера](loading-server-capacity-planning-worksheet.md) при планировании подходящее решение для загрузки.  
  
## <a name="see-also"></a>См. также  
[Обзор резервного копирования и восстановления](backup-and-restore-overview.md)  
[Обзор загрузки](load-overview.md)  
  
