---
title: Архитектура драйверов ODBC Документы Майкрософт
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
ms.openlocfilehash: 712de6a7a3f80ce1cd3ca854a88765dbfa531356
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294562"
---
# <a name="odbc-driver-architecture"></a>Архитектура драйвера ODBC
Авторы драйверов должны знать, что архитектура драйвера может повлиять на то, может ли приложение использовать специфический DBMS S'L.  
  
 ![Архитектура драйвера ODBC](../../../odbc/reference/develop-driver/media/odbcdriverovruarch.gif "ODBCDriverOvruArch")  
  
 [Драйверы на основе файлов](../../../odbc/reference/file-based-drivers.md)  
  
 Когда водитель получает доступ к физическим данным напрямую, водитель выступает как драйвер, так и источник данных. Водитель должен обрабатывать как вызовы ODBC, так и операторы S'L. Разработчики драйверов файлов должны писать свои собственные движки баз данных.  
  
 [Драйверы на основе СУБД](../../../odbc/reference/dbms-based-drivers.md)  
  
 Когда для доступа к физическим данным используется отдельный движок базы данных, драйвер обрабатывает только вызовы ODBC. Он передает операторы S'L в движок базы данных для обработки.  
  
 [Архитектура сети](../../../odbc/reference/network-example.md)  
  
 Конфигурации файлов и DBMS ODBC могут существовать в одной сети.  
  
 [Другие архитектуры драйверов](../../../odbc/reference/other-driver-architectures.md)  
  
 Когда водитель должен работать с различными источниками данных, он может быть использован в качестве промежуточного посуды. Неоднородное соединение архитектуры двигателя может сделать драйвер появляться в качестве менеджера драйвера. Драйверы также могут быть установлены на серверах, где они могут быть общими для ряда клиентов.  
  
 Для получения дополнительной информации об [Driver Architecture](../../../odbc/reference/driver-architecture.md) архитектуре драйверов [ODBC Architecture](../../../odbc/reference/odbc-architecture.md) [см.](../../../odbc/reference/the-driver-manager.md)  
  
 Более подробную информацию о проблемах драйверов можно найти в местах, описанных в следующей таблице.  
  
|Проблемы|Раздел|Расположение|  
|-----------|-----------|--------------|  
|Проблемы совместимости с приложениями и драйверами|[Приложение/совместимость драйверов](../../../odbc/reference/develop-app/application-and-driver-compatibility.md)|[Программирование Соображения](../../../odbc/reference/develop-app/programming-considerations.md), в справке программиста ODBC|  
|Написание драйверов ODBC|[Написание драйверов ODBC 3.x](../../../odbc/reference/develop-app/writing-odbc-3-x-drivers.md)|[Программирование Соображения](../../../odbc/reference/develop-app/programming-considerations.md), в справке программиста ODBC|  
|Руководящие принципы драйвера для обратной совместимости|[Рекомендации по обеспечению обратной совместимости с драйвером](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md)|[Приложение G: Руководящие принципы драйвера для обратной совместимости](../../../odbc/reference/appendixes/appendix-g-driver-guidelines-for-backward-compatibility.md), в справке программиста ODBC|  
|Подключение к водителю|[Выбор источника данных или драйвера](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)|[Подключение к источнику данных или драйверу](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)в справке программиста ODBC|  
|Выявление драйверов|[Просмотр драйверов](../../../odbc/admin/viewing-drivers.md)|[Просмотр драйверов](../../../odbc/admin/viewing-drivers.md), в Microsoft ODBC Источник данных Администратор онлайн Справка|  
|Включение объединения соединений|[Объединение подключений ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)|[Подключение к источнику данных или драйверу](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)в справке программиста ODBC|  
|Unicode/ANSI драйвера и проблемы с подключением|[Драйверы Юникода](../../../odbc/reference/develop-app/unicode-drivers.md)|[Программирование Соображения](../../../odbc/reference/develop-app/programming-considerations.md), в справке программиста ODBC|  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
