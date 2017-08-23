---
title: "Настройка общего диска кластера для SQL Server для Linux | Документы Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 92b4cb2500d4fd8a1643488593c40e97b1ff6454
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---

# <a name="shared-disk-cluster-for-sql-server-on-linux"></a>Общий диск кластера для SQL Server в Linux

Можно настроить общего хранилища кластера высокой доступности с Linux, чтобы экземпляр SQL Server для отработки отказа с одного узла на другой. В кластере типичные несколько серверов подключенной к общему хранилищу. Серверы являются узлами кластера. Отказоустойчивые кластеры обеспечивают защита на уровне экземпляра для сокращения времени восстановления, допускающей SQL Server для отработки отказа между двумя или несколькими узлами. Шаги настройки зависят от дистрибутив Linux и кластеризация решения. В следующей таблице указаны конкретные действия по проверенные кластерные решения.  

|Distribution |Раздел 
|----- |-----
|**Red Hat Enterprise Linux с надстройками высокого уровня ДОСТУПНОСТИ** |[Настройка](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Работать](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server с дополнительным высокого уровня ДОСТУПНОСТИ** |[Настройка](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>Следующие шаги


