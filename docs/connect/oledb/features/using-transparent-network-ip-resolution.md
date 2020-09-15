---
description: Использование разрешения IP-адресов прозрачной сети
title: Использование разрешения IP-адресов прозрачной сети | Документация Майкрософт
ms.custom: ''
ms.date: 01/02/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: chris-rossi
ms.author: v-chross
ms.openlocfilehash: adaad0f80d6304c855af22f134d24f0d3f23d301
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88415020"
---
# <a name="using-transparent-network-ip-resolution"></a>Использование разрешения IP-адресов прозрачной сети
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>Назначение
Разрешение IP-адресов прозрачной сети (TNIR) является исправленной версией существующей функции MultiSubnetFailover. TNIR влияет на последовательность подключений драйвера, когда первый разрешенный IP-адрес имени узла не отвечает и имеется несколько IP-адресов, связанных с именем этого узла. TNIR взаимодействует с MultiSubnetFailover и поддерживает следующие три варианта последовательности подключений.<br />
* 0: Сначала один IP-адрес, а затем все IP-адреса в параллельном режиме.
* 1: Все IP-адреса в параллельном режиме.
* 2: Все IP-адреса последовательно.

|TransparentNetworkIPResolution|MultiSubnetFailover|Поведение|
|--------|--------|--------|
|True|True|1|
|Да|Неверно|0|
|False|True|1|
|False|False|2|

## <a name="setting-transparent-network-ip-resolution"></a>Настройка разрешения IP-адресов прозрачной сети
По умолчанию transparentNetworkIPResolution имеет значение true. Параметр MultiSubnetFailover отключен по умолчанию. Дополнительные сведения об определении этих свойств см. на следующих страницах: 
- [Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server](..\applications\using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Свойства инициализации и авторизации](..\ole-db-data-source-objects\initialization-and-authorization-properties.md)

## <a name="see-also"></a>См. также: 
[Поддержка высокого уровня доступности и аварийного восстановления в драйвере OLE DB для SQL Server](./oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)
