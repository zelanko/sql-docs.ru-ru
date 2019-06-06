---
title: Перенос баз данных в SQL Server в Linux | Документация Майкрософт
description: В этой статье описываются различные варианты миграции баз данных и данных в SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1619489d-377a-4f32-8930-d4f536539689
ms.openlocfilehash: 2443611a63bee3f62ae8225384d79d34dfcb18e0
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705295"
---
# <a name="migrate-databases-and-structured-data-to-sql-server-on-linux"></a>Перенос баз данных и структурированных данных в SQL Server в Linux 

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Можно перенести базы данных и данных для SQL Server на Linux. Метод, который вы решили использовать зависит от исходных данных и от конкретного сценария. Следующие разделы содержат рекомендации для различных сценариев миграции.

## <a name="migrate-from-sql-server-on-windows"></a>Миграция из SQL Server в Windows
Если вы хотите перенести базы данных SQL Server в Windows для SQL Server в Linux, рекомендуемым способом является использование SQL Server резервного копирования и восстановления.

1. Создание резервной копии базы данных на компьютере Windows.
2. Передача файла резервной копии SQL Server Linux на целевой компьютер.
3. Восстановите резервную копию на компьютере Linux. 

Руководство по миграции базы данных с помощью резервного копирования и восстановления см. в разделе ниже:

- [Восстановление базы данных SQL Server из Windows и Linux](sql-server-linux-migrate-restore-database.md).

Можно также экспортировать базу данных в bacpac-файл (сжатый файл, содержащий схему базы данных и данных). При наличии в bacpac-файл, можно передать этот файл на компьютер Linux и затем импортировать в SQL Server. Дополнительные сведения см. в следующих разделах:

- [Экспорт и импорт базы данных с помощью SSMS или SqlPackage.exe](sql-server-linux-migrate-ssms.md)

## <a name="migrate-from-other-database-servers"></a>Миграция с других серверов баз данных
Вы можете перенести базы данных в других системах базы данных SQL Server в Linux. Это включает базы данных Microsoft Access, DB2, MySQL, Oracle и Sybase. В этом случае используйте SQL Server Management Assistant (SSMA) для автоматизации миграции на SQL Server в Linux. Дополнительные сведения см. в разделе [используйте SSMA для переноса баз данных в SQL Server на Linux](sql-server-linux-migrate-ssma.md).  

## <a name="migrate-structured-data"></a>Перенос структурированных данных
Также описаны способы импорта необработанных данных. Возможно, структурированные файлы данных, которые были экспортированы из других баз данных или источников данных. В этом случае можно использовать средство bcp для массовой вставки данных. Или можно запустить SQL Server Integration Services на Windows, чтобы импортировать данные в базу данных SQL Server в Linux. SQL Server Integration Services позволяет выполнять более сложные преобразования к данным во время импорта. 

Дополнительные сведения об этих способах см. в разделах:

- [Массовое копирование данных с помощью программы bcp](sql-server-linux-migrate-bcp.md)
- [Извлечение, преобразование и загрузка данных для SQL Server в Linux с помощью служб SSIS](sql-server-linux-migrate-ssis.md) 
