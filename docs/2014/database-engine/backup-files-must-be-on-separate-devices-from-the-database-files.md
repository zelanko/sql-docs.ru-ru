---
title: Файлы резервной копии должны находиться на разных устройствах из файлов базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 09c54c8229351cf27e0f42c8895f2633b8aa7ccb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62812628"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>Файлы резервной копии и файлы базы данных должны находиться на отдельных устройствах
  Это правило проверяет, размещаются ли файлы базы данных на устройствах отдельно от файлов резервных копий. Если файлы базы данных и файлов резервных копий расположены на одном устройстве, то в случае его сбоя резервные копии будут недоступны. Кроме того, размещение файлов базы данных и файлов резервных копий на отдельных устройствах оптимизирует производительность ввода-вывода как при записи резервных копий, так и в процессе эксплуатации базы данных.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Настоятельно рекомендуется размещать базу данных и резервные копии на отдельных устройствах резервного копирования.  
  
> [!NOTE]  
>  Эта политика не может обнаружить отдельные физические устройства посредством точек подключения.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Устройства резервного копирования &#40;SQL Server&#41;](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [Резервное копирование и восстановление баз данных SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
