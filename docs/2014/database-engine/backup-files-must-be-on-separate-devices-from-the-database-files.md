---
title: Файлы резервной копии должен находиться на отдельных устройствах файлы базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
caps.latest.revision: 12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18b1f6d38f67dacc2a8da06a061d6bd76e055196
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818110"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>Файлы резервной копии и файлы базы данных должны находиться на отдельных устройствах
  Это правило проверяет, размещаются ли файлы базы данных на устройствах отдельно от файлов резервных копий. Если файлы базы данных и файлов резервных копий расположены на одном устройстве, то в случае его сбоя резервные копии будут недоступны. Кроме того, размещение файлов базы данных и файлов резервных копий на отдельных устройствах оптимизирует производительность ввода-вывода как при записи резервных копий, так и в процессе эксплуатации базы данных.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Настоятельно рекомендуется размещать базу данных и резервные копии на отдельных устройствах резервного копирования.  
  
> [!NOTE]  
>  Эта политика не может обнаружить отдельные физические устройства посредством точек подключения.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Устройства резервного копирования (SQL Server)](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [Резервное копирование и восстановление баз данных SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
