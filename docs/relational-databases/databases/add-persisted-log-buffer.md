---
description: Добавление буфера сохраненного журнала в базу данных
title: Добавление буфера сохраненного журнала в базу данных
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- PMEM
- persistent memory
- persisted log buffer
- add log file
- create log buffer
- remove log buffer
ms.assetid: 8ead516a-1334-4f40-84b2-509d0a8ffa45
author: briancarrig
ms.author: brcarrig
manager: amitban
ms.openlocfilehash: cf3289d9d233da56c22739d3912045c2cdaa7554
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476253"
---
# <a name="add-persisted-log-buffer-to-a-database"></a>Добавление буфера сохраненного журнала в базу данных
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этом разделе описывается добавление буфера сохраненного журнала в базу данных в [!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="permissions"></a>Разрешения

Необходимо разрешение ALTER на базу данных.  

## <a name="configure-persistent-memory-device-linux"></a>Настройка устройства энергонезависимой памяти (Linux)

Настройка устройства энергонезависимой памяти в [Linux](../../linux/sql-server-linux-configure-pmem.md).

## <a name="configure-persistent-memory-device-windows"></a>Настройка устройства энергонезависимой памяти (Windows)

Настройка устройства энергонезависимой памяти в [Windows](/windows-server/storage/storage-spaces/deploy-pmem/).
  
## <a name="add-a-persisted-log-buffer-to-a-database"></a>Добавление буфера сохраненного журнала в базу данных  

В следующих примерах добавляется буфер сохраненного журнала.

```sql
ALTER DATABASE <MyDB> 
  ADD LOG FILE 
  (
    NAME = <DAXlog>, 
    FILENAME = '<Filepath to DAX Log File>', 
    SIZE = 20MB
  );
```

Том или точка подключения нового файла журнала должны быть отформатированы с помощью DAX (NTFS) или подключены с параметром DAX (XFS и EXT4).

## <a name="remove-a-persisted-log-buffer"></a>Удаление буфера сохраненного журнала

Чтобы безопасно удалить буфер сохраненного журнала, база данных должна быть помещена в однопользовательский режим, чтобы можно было освободить буфер сохраненного журнала.

В следующем примере удаляется буфер сохраненного журнала.

```sql
ALTER DATABASE <MyDB> SET SINGLE_USER;
ALTER DATABASE <MyDB> REMOVE FILE <DAXlog>;
ALTER DATABASE <MyDB> SET MULTI_USER;
```

## <a name="limitations"></a>Ограничения

[Прозрачное шифрование данных (TDE)](../security/encryption/transparent-data-encryption.md) несовместимо с буфером сохраненного журнала.

[Группы доступности](../../t-sql/statements/create-availability-group-transact-sql.md) могут использовать эту функцию только на вторичных репликах из-за необходимости в обычной семантике записи в журнал на первичном сервере. Однако небольшой файл журнала должен быть создан на всех узлах (в идеале на томах или точках подключения DAX).

## <a name="backup-and-restore-operations"></a>Операции резервного копирования и восстановления

Применяются обычные условия восстановления. Если буфер сохраненного журнала восстанавливается или монтируется на томе DAX, он продолжит функционировать; в противном случае его можно безопасно удалить.
  
## <a name="next-steps"></a>Дальнейшие действия

- [Как это работает (просто выполняется быстрее): кэширование заключительного фрагмента журнала SQL Server в непостоянной памяти на устройстве NVDIMM](https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/)
- [Представлены данные: задержка и устойчивость в SQL Server 2016](https://channel9.msdn.com/Shows/Data-Exposed/Latency-and-Durability-with-SQL-Server-2016)
- [Сокращение задержки фиксации транзакций с помощью памяти класса хранилища в Windows Server 2016 и SQL Server 2016 с пакетом обновления 1 (SP1)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/12/02/transaction-commit-latency-acceleration-using-storage-class-memory-in-windows-server-2016sql-server-2016-sp1/)
