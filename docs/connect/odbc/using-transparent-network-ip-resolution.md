---
title: С помощью разрешение IP-адресов для прозрачной сети | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7249d00dc4f3d71b7c3245e2939be7e541f5b39
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-transparent-network-ip-resolution"></a>С помощью прозрачного сетевого разрешение IP-адресов
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution является существующей MultiSubnetFailover функции, доступные в Microsoft ODBC Driver 13.1 for SQL Server, которая влияет на время подключения драйвера там, где первый разрешить IP-адрес имени узла не поддерживает версии ответ и имеется несколько IP-адресов, связанный с именем узла. Он взаимодействует с MultiSubnetFailover для предоставления следующих трех соединения последовательностей:

* 0: один предпринимается IP, следуют все IP-адресов в параллельном режиме
* 1: попытка всех IP-адресов в параллельном режиме
* 2: применяются все IP-адреса друг за другом

|TransparentNetworkIPResolution|MultiSubnetFailover|Поведение|
|:-:|:-:|:-:|
|(по умолчанию).|(по умолчанию).|0|
|(по умолчанию).|Включено|1|
|(по умолчанию).|Выключено|0|
|Включено|(по умолчанию).|0|
|Включено|Включено|1|
|Включено|Выключено|0|
|Выключено|(по умолчанию).|2|
|Выключено|Включено|1|
|Выключено|Выключено|2|

`TransparentNetworkIPResolution` Строку соединения и источника данных определяет ключевое слово, этот параметр на уровне строки подключения. По умолчанию включен.

Ключевое слово|Значения|По умолчанию
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

`SQL_COPT_SS_TNIR` Атрибута предварительного соединения позволяет приложению управлять программным образом этот параметр:

Атрибут соединения|   Размер или тип|  По умолчанию| Значение| Описание
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER`или`SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Включает или отключает TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Дополнительные сведения о MultiSubnetFailover см. в разделе [драйвер ODBC для Linux и macOS - высокого уровня доступности и аварийного восстановления](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a>См. также  
* [Драйвер Microsoft ODBC Driver for SQL Server в Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [SQL Server с несколькими подсетями кластеризация (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
