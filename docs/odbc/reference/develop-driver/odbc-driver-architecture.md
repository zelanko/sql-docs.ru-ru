---
description: Архитектура драйвера ODBC
title: Архитектура драйвера ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], architecture
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1789d5799ed9eb15ace7ea263d1a5804c8e86e74
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476250"
---
# <a name="odbc-driver-architecture"></a>Архитектура драйвера ODBC
Модули записи драйверов должны знать, что архитектура драйвера может повлиять на то, может ли приложение использовать специфический для СУБД SQL.  
  
 ![Архитектура драйвера ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "одбкдриверовруарч")  
  
 [Драйверы на основе файлов](../../../odbc/reference/file-based-drivers.md)  
  
 Когда драйвер обращается непосредственно к физическим данным, драйвер действует как драйвер, так и источник данных. Драйвер должен обрабатывать как вызовы ODBC, так и инструкции SQL. Разработчики файловых драйверов должны писать собственные ядра СУБД.  
  
 [Драйверы на основе СУБД](../../../odbc/reference/dbms-based-drivers.md)  
  
 Если для доступа к физическим данным используется отдельное ядро СУБД, драйвер обрабатывает только вызовы ODBC. Он передает инструкции SQL ядру СУБД для обработки.  
  
 [Сетевая архитектура](../../../odbc/reference/network-example.md)  
  
 Конфигурации файлов и СУБД ODBC могут существовать в одной сети.  
  
 [Другие архитектуры драйверов](../../../odbc/reference/other-driver-architectures.md)  
  
 Если драйвер необходим для работы с различными источниками данных, его можно использовать по промежуточного слоя. Архитектура разнородного механизма объединения может привести к отображению драйвера в качестве диспетчера драйверов. Драйверы также могут быть установлены на серверах, где они могут совместно использоваться несколькими клиентами.  
  
 Дополнительные сведения об архитектуре драйвера см. в разделе Архитектура [диспетчера драйверов](../../../odbc/reference/the-driver-manager.md) и [драйвера](../../../odbc/reference/driver-architecture.md) раздела об [архитектуре ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Дополнительные сведения о проблемах с драйверами можно найти в расположениях, описанных в следующей таблице.  
  
|Проблема|Раздел|Расположение|  
|-----------|-----------|--------------|  
|Проблемы совместимости с приложениями и драйверами|[Совместимость приложений и драйверов](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Рекомендации по программированию](../../../odbc/reference/develop-app/programming-considerations.md)в справочнике программиста по ODBC|  
|Написание драйверов ODBC|[Написание драйверов ODBC 3.x](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Рекомендации по программированию](../../../odbc/reference/develop-app/programming-considerations.md)в справочнике программиста по ODBC|  
|Рекомендации по драйверам для обеспечения обратной совместимости|[Рекомендации по обеспечению обратной совместимости с драйвером](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Приложение ж. рекомендации по использованию драйверов для обеспечения обратной совместимости](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)в справочнике программиста по ODBC|  
|Подключение к драйверу|[Выбор источника данных или драйвера](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Подключение к источнику данных или драйверу](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), Справочник программиста по ODBC|  
|Определение драйверов|[Просмотр драйверов](../../../odbc/admin/viewing-drivers.md)|[Просмотр драйверов](../../../odbc/admin/viewing-drivers.md)в интерактивной справке администратора источников данных Microsoft ODBC|  
|Включение пулов соединений|[Объединение соединений ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Подключение к источнику данных или драйверу](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), Справочник программиста по ODBC|  
|Проблемы с подключением и драйверами Юникода/ANSI|[Драйверы Юникода](../../../odbc/reference/develop-app/unicode-drivers.md)|[Рекомендации по программированию](../../../odbc/reference/develop-app/programming-considerations.md)в справочнике программиста по ODBC|  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
