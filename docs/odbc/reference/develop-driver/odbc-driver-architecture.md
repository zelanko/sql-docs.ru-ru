---
title: "Архитектура драйвера ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], architecture
ms.assetid: 21a62c7c-192e-4718-a16e-aa12b0de4419
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 39477161fd3eac02912fd371a873b94ea9f51828
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-driver-architecture"></a>Архитектура драйвера ODBC
Авторы драйвер необходимо иметь в виду, что архитектура драйвера могут повлиять на приложения, могут ли использовать СУБД SQL.  
  
 ![Архитектура драйвера ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Драйверов на основе файлов](../../../odbc/reference/file-based-drivers.md)  
  
 Когда драйвер обращается к физических данных напрямую, драйвер выступает в качестве источника данных и драйвера. Драйвер должен обрабатывать вызовы ODBC и инструкций SQL. Разработчики драйверов на основе файлов должны создавать свои собственные модули базы данных.  
  
 [Драйверов на основе DBMS](../../../odbc/reference/dbms-based-drivers.md)  
  
 При использовании для доступа к данным физических отдельное ядро СУБД драйвер обрабатывает только вызовы ODBC. Он передает инструкции SQL database engine для обработки.  
  
 [Архитектура сети](../../../odbc/reference/network-example.md)  
  
 Конфигурации файла и СУБД ODBC могут существовать в одной сети.  
  
 [Других архитектур драйвера](../../../odbc/reference/other-driver-architectures.md)  
  
 Если драйвер необходим для работы с различными источниками данных, он может использоваться как по промежуточного слоя. Архитектура ядра СУБД разнородных соединения можно сделать драйвера, которые отображаются в виде диспетчера драйверов. Драйверы также может устанавливаться на серверах, где они могут совместно использоваться ряд клиентов.  
  
 Дополнительные сведения об архитектуре драйвера см. в разделе [диспетчера драйверов](../../../odbc/reference/the-driver-manager.md) и [архитектура драйвера](../../../odbc/reference/driver-architecture.md) в разделе [архитектура ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Дополнительные сведения о драйверов можно найти в местах, описанных в следующей таблице.  
  
|Проблема|Раздел|Местоположение|  
|-----------|-----------|--------------|  
|Проблемы совместимости приложений и драйверов|[Совместимость приложений и драйверов](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Рекомендации по программированию](../../../odbc/reference/develop-app/programming-considerations.md), в справочнике программиста ODBC|  
|Драйверы ODBC записи|[Написание ODBC 3.x драйверы](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Рекомендации по программированию](../../../odbc/reference/develop-app/programming-considerations.md), в справочнике программиста ODBC|  
|Рекомендации по драйверов для обеспечения обратной совместимости|[Рекомендации по драйверов для обеспечения обратной совместимости](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Приложение ж драйвер рекомендации для обеспечения обратной совместимости](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), в справочнике программиста ODBC|  
|Подключение к драйвера|[Выбор данных источника или драйвер](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Подключение к данным источника или драйвер](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), в справочнике программиста ODBC|  
|Определение драйверов|[Просмотр драйверов](../../../odbc/admin/viewing-drivers.md)|[Просмотр драйверы](../../../odbc/admin/viewing-drivers.md), в интерактивной справке администратора источников данных ODBC|  
|Включение пулов соединений|[Организация пулов соединений ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Подключение к данным источника или драйвер](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md), в справочнике программиста ODBC|  
|Unicode-ANSI драйвера и проблем с подключением|[Драйверы Юникода](../../../odbc/reference/develop-app/unicode-drivers.md)|[Рекомендации по программированию](../../../odbc/reference/develop-app/programming-considerations.md), в справочнике программиста ODBC|  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
