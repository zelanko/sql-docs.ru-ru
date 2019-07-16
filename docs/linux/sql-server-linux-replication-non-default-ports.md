---
title: Настройка общих папок моментального снимка репликации SQL Server в Linux
description: В этой статье описывается, как настроить репликацию моментальных снимков папки общих ресурсов SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6959b2073871f70fb33823b50419c208a23df2dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093186"
---
# <a name="configure-replication-with-non-default-ports"></a>Настройка репликации с портами не по умолчанию

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Вы можете настроить репликацию с помощью SQL Server на прослушивание любого порта, настроенного с помощью параметра mssql-conf network.tcpport экземпляров Linux. Порт должен добавляться к имени сервера во время настройки, если выполняются следующие условия:

1. Настройки репликации включает экземпляр SQL Server в Linux
2. Любой экземпляр (Windows или Linux), прослушивает порт не по умолчанию. 

Имя сервера экземпляра можно найти, выполнив @@servername на экземпляре.

## <a name="examples"></a>Примеры

«Server1» осуществляет прослушивание порта 1500 на платформе Linux. Чтобы настроить «Server1» для распространения, выполните `sp_adddistributor` с `@distributor`. Пример: 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

«Server1» осуществляет прослушивание порта 1500 на платформе Linux. Чтобы настроить издатель на распространителе, запустите `sp_adddistpublisher` с `@publisher`. Пример:

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

«Server2» прослушивает порт 6549 в Linux. Чтобы настроить «Server2» в качестве подписчика, запустите `sp_addsubscription` с `@subscriber`. Пример:

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

«Server3» прослушивает порт 6549 в Windows с именем сервера Server3 и имя экземпляра MSSQL2017. Чтобы настроить «Server3» в качестве подписчика, запустите `sp_addsubscription` с `@subscriber`. Пример:

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>Следующие шаги

[Основные понятия: Репликация SQL Server в Linux](sql-server-linux-replication.md)

[Хранимые процедуры репликации](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

