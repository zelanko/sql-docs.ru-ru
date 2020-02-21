---
title: Настройка свойств источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0b3093b87557917655fcbfd6cf7c2ec37151ca44
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027727"
---
# <a name="setting-the-data-source-properties"></a>Настройка свойств источника данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Источники данных являются предпочтительным механизмом, с помощью которого создаются соединения JDBC на платформе Java в среде Enterprise Edition (Java EE). Источники данных предоставляют соединения, пулы соединений, распределенные соединения, и для этого не нужно использовать жестко запрограммированные свойства соединения на коде Java. Все источники данных [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] могут устанавливать или принимать значения всех свойств с помощью соответствующих методов задания и получения значений.

Продукты Java EE, например серверы приложений и обработчики сервлетов/JSP, как правило, позволяют настроить источники данных для доступа к базе данных. Все свойства, перечисленные в разделе [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md), могут быть заданы там, где конфигурация позволяет вводить свойства в виде пар "свойство=значение".

Дополнительные сведения об источниках данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в описании класса [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). Например, сведения об использовании класса SQLServerDataSource для установки подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Data source sample](../../connect/jdbc/data-source-sample.md) (Пример источника данных).

## <a name="see-also"></a>См. также раздел

[Подключение к SQL Server с помощью JDBC Driver](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
