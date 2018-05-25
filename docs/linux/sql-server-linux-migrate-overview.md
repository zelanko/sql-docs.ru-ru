---
title: Перенос баз данных в SQL Server для Linux | Документы Microsoft
description: В этой статье описываются различные варианты миграции баз данных и данных в SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 1619489d-377a-4f32-8930-d4f536539689
ms.custom: sql-linux
ms.openlocfilehash: c7b7225ae4e981244ee06194ea9e4ef595ba283d
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="migrate-databases-and-structured-data-to-sql-server-on-linux"></a>Перенос баз данных и структурированных данных в SQL Server в Linux 

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Можно перенести базы данных и данных для SQL Server 2017 г., выполняемым на платформе Linux. Метод, который вы решили использовать зависит от источника данных и конкретного сценария. В следующих разделах содержатся советы и рекомендации для различных сценариев миграции.

## <a name="migrate-from-sql-server-on-windows"></a>Миграция из SQL Server в Windows
Если вы хотите перенести базы данных SQL Server в Windows 2017 г. SQL Server в Linux, рекомендуемая методика — использовать SQL Server резервного копирования и восстановления.

1. Создайте резервную копию базы данных на компьютере Windows.
2. Передача файла резервной копии SQL Server Linux на целевой компьютер.
3. Восстановите резервную копию на компьютере Linux. 

Руководство по миграции базы данных путем резервного копирования и восстановления см. в разделе:

- [Восстановление базы данных SQL Server из Windows, Linux](sql-server-linux-migrate-restore-database.md).

Можно также экспортировать базу данных в файл BACPAC (сжатый файл, содержащий схему базы данных и данных). Если имеется файл BACPAC, можно передать этот файл на компьютер Linux и затем импортировать в SQL Server. Дополнительные сведения см. в следующих разделах:

- [Экспорт и импорт базы данных с помощью SSMS или SqlPackage.exe](sql-server-linux-migrate-ssms.md)

## <a name="migrate-from-other-database-servers"></a>Миграция с другими серверами баз данных
Можно перенести базы данных на другие базы данных системы 2017 г. SQL Server в Linux. Это включает базы данных Microsoft Access, DB2, MySQL, Oracle и Sybase. В этом случае используйте SQL Server Management Assistant (SSMA) для автоматического перехода на SQL Server в Linux. Дополнительные сведения см. в разделе [используйте SSMA для переноса баз данных в SQL Server в Linux](sql-server-linux-migrate-ssma.md).  

## <a name="migrate-structured-data"></a>Перенос структурированных данных
Также описаны способы импорта необработанных данных. Возможно, структурированных файлов данных, которые были экспортированы из других баз данных или источников данных. В этом случае можно использовать программу bcp для массовой вставки данных. Либо можно запускать SQL Server Integration Services в Windows для импорта данных в базу данных SQL Server в Linux. SQL Server Integration Services позволяет выполнять более сложные преобразования данных во время импорта. 

Дополнительные сведения об этих способах см. в следующих разделах:

- [Массовое копирование данных с помощью программы bcp](sql-server-linux-migrate-bcp.md)
- [Извлечения, преобразования и загрузки данных для SQL Server в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md) 
