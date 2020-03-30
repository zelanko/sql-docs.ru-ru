---
title: Настройка папки моментальных снимков репликации (порты не по умолчанию)
titleSuffix: SQL Server on Linux
description: Узнайте, как настроить общие папки моментальных снимков с портами, отличными от портов по умолчанию, для репликации SQL Server на Linux.
ms.custom: seo-lt-2019
author: MikeRayMSFT
ms.author: mikerayW
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: cb715e2a0a056c18352361b58ce8ffd67e3da78e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75558599"
---
# <a name="configure-replication-with-non-default-ports-sql-server-linux"></a>Настройка репликации с использованием портов, отличных от портов по умолчанию (SQL Server на Linux)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

При репликации экземпляры SQL Server на Linux могут ожидать передачи данных через любой порт, настроенный с параметром mssql-conf network.tcpport. Во время настройки номер порта необходимо добавить к имени сервера, если выполняются указанные ниже условия.

1. В конфигурации репликации имеется экземпляр SQL Server на Linux.
2. Любой экземпляр (Windows или Linux) ожидает передачи данных через порт, отличный от порта по умолчанию. 

Имя сервера экземпляра можно узнать, выполнив команду @@servername в экземпляре.

## <a name="examples"></a>Примеры

Server1 ожидает передачи данных через порт 1500 в Linux. Чтобы настроить Server1 для распространения, выполните хранимую процедуру `sp_adddistributor` с аргументом `@distributor`. Пример: 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

Server1 ожидает передачи данных через порт 1500 в Linux. Чтобы настроить издатель для распространителя, выполните хранимую процедуру `sp_adddistpublisher` с аргументом `@publisher`. Пример:

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

Server2 ожидает передачи данных через порт 6549 в Linux. Чтобы настроить Server2 в качестве подписчика, выполните хранимую процедуру `sp_addsubscription` с аргументом `@subscriber`. Пример:

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

Server3 ожидает передачи данных через порт 6549 в Windows с именем сервера Server3 и именем экземпляра MSSQL2017. Чтобы настроить Server3 в качестве подписчика, выполните хранимую процедуру `sp_addsubscription` с аргументом `@subscriber`. Пример:

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>Дальнейшие действия

[Основные понятия. Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

