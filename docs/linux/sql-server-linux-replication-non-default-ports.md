---
title: Настройка репликации общих папок моментальных снимков в SQL Server на Linux
description: В этой статье описывается настройка репликации общих папок моментальных снимков в SQL Server на Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6959b2073871f70fb33823b50419c208a23df2dd
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68093186"
---
# <a name="configure-replication-with-non-default-ports"></a>Настройка репликации с использованием портов, отличных от портов по умолчанию

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

## <a name="next-steps"></a>Следующие шаги

[Основные понятия. Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

