---
description: Поддержка высокого уровня доступности и аварийного восстановления драйверов Майкрософт для PHP для SQL Server
title: Поддержка высокого уровня доступности и аварийного восстановления драйверов Майкрософт для PHP для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 875c5944a0b74c7140843388da1e783e9f2ba5b8
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726766"
---
# <a name="support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этом разделе приведены сведения о поддержке в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] (начиная с версии 3.0) аварийного восстановления и высокой доступности.

Для драйверов Майкрософт для PHP для SQL Server, начиная с версии 3.0, в качестве сервера в строке подключения можно указать прослушиватель группы доступности с высокой доступностью, группу доступности с возможностью аварийного восстановления или экземпляр кластера отработки отказа.

Свойство подключения **MultiSubnetFailover** указывает, что приложение развертывается в группе доступности или экземпляре отказоустойчивого кластера, а также что драйвер попытается подключиться ко всем IP-адресам базы данных в первичном экземпляре SQL Server. Всегда задавайте **MultiSubnetFailover=True** при подключении к прослушивателю группы доступности или экземпляру отказоустойчивого кластера SQL Server. Если приложение подключается к базе данных AlwaysOn, которая выполняет отработку отказа, то первоначальное подключение разрывается и приложение должно открыть новое подключение, чтобы продолжить работу после обработки отказа.

Подробные сведения о группе доступности Always On можно найти на странице документации [SQL Server Native Client Support for High Availability, Disaster Recovery](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md) (Поддержка SQL Server Native Client для высокого уровня доступности и аварийного восстановления).

## <a name="transparent-network-ip-resolution-tnir"></a>Прозрачное разрешение IP-адресов сети (TNIR)

Разрешение IP-адресов прозрачной сети (TNIR) является исправленной версией существующей функции **MultiSubnetFailover**. Это влияет на последовательность подключений драйвера, когда первый разрешенный IP-адрес имени узла не отвечает и имеется несколько IP-адресов, связанных с именем этого узла. Соответствующий параметр соединения — **TransparentNetworkIPResolution**. Вместе с **MultiSubnetFailover** он предоставляет следующие четыре последовательности подключения. 

- TNIR — включено и **MultiSubnetFailover** — отключено: сначала один IP-адрес, а затем все IP-адреса в параллельном режиме.
- TNIR — включено и **MultiSubnetFailover** — включено: все IP-адреса в параллельном режиме.
- TNIR — отключено и **MultiSubnetFailover** — отключено: все IP-адреса последовательно.
- TNIR — отключено и **MultiSubnetFailover** — включено: все IP-адреса в параллельном режиме.

По умолчанию TNIR включено, а **MultiSubnetFailover** — отключено.

Ниже приведен пример включения TNIR и **MultiSubnetFailover** с помощью драйвера PDO_SQLSRV.

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$connectionString = "sqlsrv:Server=$serverName; TransparentNetworkIPResolution=Enabled; MultiSubnetFailover=yes";
try {
    $conn = new PDO($connectionString, $username, $password, array(PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION));
    // your code 
    // more of your code
    // when done, close the connection
    unset($conn);
} catch(PDOException $e) {
    print_r($e->errorInfo);
}
?>
```

## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Переход с зеркального отображения базы данных на использование кластеров с несколькими подсетями  
Если в строке подключения содержатся ключевые слова **MultiSubnetFailover** и **Failover_Partner**, то при соединении произойдет ошибка. Ошибка возникает также в том случае, если используется **MultiSubnetFailover** и SQL Server возвращает ответ партнера по обеспечению отработки отказа, указывающий на то, что он является частью пары зеркальных баз данных.  
  
При переводе приложения PHP, которое сейчас использует зеркальное отображение базы данных, на сценарий с использованием множества подсетей необходимо удалить свойство подключения **Failover_Partner**, заменив его свойством **MultiSubnetFailover** со значением **True**, а имя сервера в строке подключения — прослушивателем группы доступности. Если в строке подключения используются **Failover_Partner** и **MultiSubnetFailover=true**, то драйвер выдаст ошибку. Но если в строке подключения используются параметры **Failover_Partner** и **MultiSubnetFailover=false** (или **ApplicationIntent=ReadWrite**), то приложение будет использовать зеркальное отображение базы данных.  
  
Если зеркальное отображение базы данных применяется к базе данных-источнику группы доступности, то драйвер вернет ошибку. Это также произойдет при использовании параметра **MultiSubnetFailover=true** в строке подключения, относящейся к базе данных-источнику, а не к прослушивателю группы доступности.  

[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="see-also"></a>См. также:  
[Подключение к серверу](../../connect/php/connecting-to-the-server.md)  
