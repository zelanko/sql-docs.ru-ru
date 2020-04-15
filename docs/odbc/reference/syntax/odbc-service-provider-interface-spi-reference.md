---
title: Интерфейс поставщика услуг ODBC (SPI) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e9739abd13bf2c4bed1b1b3a31c18c683594705a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298912"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>Справочник по интерфейсу службы доступа (SPI) ODBC
Традиционно ODBC определил интерфейс программирования приложений (API). Функции в API могут быть вызваны приложениями, и они должны быть реализованы как внутри менеджера драйвера, так и драйвера.  
  
 С добавлением функции объединения соединения, осведомленной о драйвере, ODBC вводит интерфейс поставщика услуг (SPI). Функции в SPI используются для связи между менеджером водителя и водителем. Функции SPI выполняются водителем; Менеджер драйвера не предоставляет приложениям функции SPI. Приложения не должны вызывать эти функции напрямую.  
  
 Включите sqlspi.h для разработки драйверов ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [СЗЛКCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [СЗЛГетПулИД](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [СЗЛПулКоннект](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [Соединение СЗЛРатЕ](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [СЗЛСетКоннекаттаттПродбИнФО](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [СЗЛСетКоннекинфо](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [СЗЛСетДрайверКоннинфо](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Разработка осведомленности о подключении-пуле в драйвере ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Организация пулов соединений диспетчера драйверов](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
