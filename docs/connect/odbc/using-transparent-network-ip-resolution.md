---
title: С помощью разрешение IP-адресов прозрачной сети | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 94c7f34ebf66f4bf33acf51e44397a74de2367e0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801719"
---
# <a name="using-transparent-network-ip-resolution"></a>Использование разрешения IP-адресов прозрачной сети
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution является редакцией MultiSubnetFailover функцией, доступные в Microsoft ODBC Driver 13.1 for SQL Server, который влияет на время подключения драйвера в случае, когда первый разрешенный IP-адрес имени узла не поддерживает ответ, и существует несколько IP-адресов, связанный с именем узла. Он взаимодействует с MultiSubnetFailover для предоставления следующие три подключения последовательности:

* 0: один IP-адрес предпринимается, следуют все IP-адреса в параллельном режиме
* 1: все IP-адреса попытки подключения выполняются в параллельном режиме
* 2: все IP-адреса попытки подключения выполняются один за другим

|TransparentNetworkIPResolution|MultiSubnetFailover|Поведение|
|:-:|:-:|:-:|
|(по умолчанию).|(по умолчанию).|0|
|(по умолчанию).|Активировано|1|
|(по умолчанию).|Выключено|0|
|Активировано|(по умолчанию).|0|
|Активировано|Активировано|1|
|Активировано|Выключено|0|
|Выключено|(по умолчанию).|2|
|Выключено|Активировано|1|
|Выключено|Выключено|2|

`TransparentNetworkIPResolution` Строку подключения и имени DSN ключевое слово управляет этот параметр на уровне строки подключения. По умолчанию включен.

Ключевое слово|Значения|По умолчанию
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

`SQL_COPT_SS_TNIR` Атрибута предварительного соединения позволяет приложению для управления, этот параметр, программным способом:

Атрибут подключения|   Размер и тип|  По умолчанию| Значение| Описание
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` либо `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Включает или отключает TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Дополнительные сведения о MultiSubnetFailover, см. в разделе [драйвер ODBC для Linux и macOS — высокий уровень доступности и аварийного восстановления](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a>См. также:  
* [Драйвер Microsoft ODBC Driver for SQL Server в Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [Кластеры SQL Server с несколькими подсетями (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
