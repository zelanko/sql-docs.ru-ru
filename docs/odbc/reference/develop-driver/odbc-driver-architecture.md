---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5d123bdf1ea3357a4846a223c41950c952c1af2d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915534"
---
# <a name="odbc-driver-architecture"></a>Архитектура драйвера ODBC
Драйвер модулей записи необходимо иметь в виду, что архитектура драйвера могут повлиять на приложения, могут ли использовать СУБД SQL.  
  
 ![Архитектура драйвера ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Драйверы на основе файла](../../../odbc/reference/file-based-drivers.md)  
  
 Когда драйвер обращается напрямую к физических данных, драйвер выступает в качестве источника данных и драйвера. Драйвер должен обрабатывать вызовы ODBC и инструкций SQL. Разработчики драйверов на основе файлов должны создавать свои собственные модули базы данных.  
  
 [Драйверы на основе СУБД](../../../odbc/reference/dbms-based-drivers.md)  
  
 Если отдельный механизм СУБД используется для доступа к физическим перемещением данных, драйвер обрабатывает только вызовы ODBC. Он передает инструкции SQL database engine для обработки.  
  
 [Архитектура сети](../../../odbc/reference/network-example.md)  
  
 Конфигурации файла и СУБД ODBC могут существовать в одной сети.  
  
 [Другие архитектуры драйверов](../../../odbc/reference/other-driver-architectures.md)  
  
 Если драйвер необходим для работы с различными источниками данных, он может использоваться как по промежуточного слоя. Архитектура ядра СУБД разнородных соединения можно сделать драйвер устройства отображаются в виде диспетчера драйверов. Драйверы можно также установить на серверах, где они могут совместно использоваться ряда клиентов.  
  
 Дополнительные сведения об архитектуре драйвера см. в разделе [диспетчера драйверов](../../../odbc/reference/the-driver-manager.md) и [архитектура драйвера](../../../odbc/reference/driver-architecture.md) в разделе, посвященном [архитектура ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Дополнительные сведения о драйверов можно найти в местах, описанных в следующей таблице.  
  
|Проблемы|Раздел|Location|  
|-----------|-----------|--------------|  
|Проблемы совместимости с приложениями и драйверами|[Совместимость приложений и драйверов](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Замечания по программированию](../../../odbc/reference/develop-app/programming-considerations.md), справочника по программированию ODBC|  
|Написание драйверов ODBC|[Написание драйверов ODBC 3.x](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Замечания по программированию](../../../odbc/reference/develop-app/programming-considerations.md), справочника по программированию ODBC|  
|Рекомендации по драйверов для обеспечения обратной совместимости|[Рекомендации по драйверов для обеспечения обратной совместимости](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Приложение ж Рекомендации по драйверов для обеспечения обратной совместимости](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), справочника по программированию ODBC|  
|Подключение к драйвера|[Выбор источника данных или драйвера](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Подключение к данным источника или драйвер](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), справочника по программированию ODBC|  
|Определение драйверов|[Просмотр драйверов](../../../odbc/admin/viewing-drivers.md)|[Просмотр драйверов](../../../odbc/admin/viewing-drivers.md), интерактивной справки администратора источников данных ODBC|  
|Включение организация пулов соединений|[Организация пулов соединений ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Подключение к данным источника или драйвер](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), справочника по программированию ODBC|  
|Юникода/ANSI драйвера и проблем с подключением|[Драйверы Юникода](../../../odbc/reference/develop-app/unicode-drivers.md)|[Замечания по программированию](../../../odbc/reference/develop-app/programming-considerations.md), справочника по программированию ODBC|  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
