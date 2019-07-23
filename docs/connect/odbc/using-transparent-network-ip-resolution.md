---
title: Использование разрешения IP-адресов в прозрачной сети | Документация Майкрософт
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
ms.openlocfilehash: df5b0233168c52b4f79cdc6d2d03cd7b72e16046
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008486"
---
# <a name="using-transparent-network-ip-resolution"></a>Использование разрешения IP-адресов прозрачной сети
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution — это редакция существующей функции MultiSubnetFailover, доступная в драйвере Microsoft ODBC 13,1 для SQL Server, которая влияет на последовательность подключения драйвера в случае, когда первый разрешенный IP-адрес имени узла не ответ, и существует несколько IP-адресов, связанных с именем узла. Он взаимодействует с MultiSubnetFailover для предоставления следующих трех последовательностей соединений:

* 0 — предпринята одна IP-часть, за которой следуют все адреса в параллельном режиме
* 1: все IP-адреса попытаются параллельно
* 2: все IP-адреса попытаются один за другим

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

Строка `TransparentNetworkIPResolution` подключения и ключевое слово DSN контролирует этот параметр на уровне строки соединения. Значение по умолчанию — Enabled.

Ключевое слово|Значения|По умолчанию
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

Атрибут `SQL_COPT_SS_TNIR` предварительного подключения позволяет приложению управлять этим параметром программным способом:

Атрибут подключения|   Размер и тип|  По умолчанию| Значение| Описание
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` либо `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Включает или отключает ТНИР.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Дополнительные сведения о MultiSubnetFailover см. [в статье драйвер ODBC в Linux и macOS — высокий уровень доступности и аварийное восстановление](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md) .
--------------------------------------------------
## <a name="see-also"></a>См. также:  
* [Драйвер Microsoft ODBC Driver for SQL Server в Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [Кластеры SQL Server с несколькими подсетями (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
