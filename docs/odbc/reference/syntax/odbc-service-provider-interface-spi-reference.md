---
title: Справочник по интерфейсу поставщика служб ODBC (SPI) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 88053620fa413c50a8faff4cc47cbbe1457249f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073833"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>Справочник по интерфейсу службы доступа (SPI) ODBC
Обычно ODBC определяет интерфейс программирования приложений (API). Функции в API могут вызываться приложениями и должны быть реализованы в диспетчере драйверов и драйвере.  
  
 С добавлением функции пулов соединений с учетом драйверов ODBC вводит интерфейс поставщика услуг (SPI). Функции в индексе SPI используются для обмена данными между диспетчером драйверов и драйвером. Функции SPI реализуются драйвером. Диспетчер драйверов не предоставляет приложениям функции SPI. Приложения не должны вызывать эти функции напрямую.  
  
 Включите склспи. h для разработки драйвера ODBC.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [склклеанупконнектионпулид](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [склжетпулид](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [склпулконнект](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [склратеконнектион](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [склсетконнектаттрфордбЦинфо](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [склсетконнектинфо](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [склсетдриверконнектинфо](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Разработка осведомленности о пуле подключений в драйвере ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Организация пулов соединений диспетчера драйверов](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
