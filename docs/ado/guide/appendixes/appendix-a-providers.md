---
title: Приложение а. поставщики | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5110c06913325421aeeaa2d31295d7e2bc6bf59c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645602"
---
# <a name="appendix-a-data-and-service-providers"></a>Приложение а данных и поставщики услуг
В этом разделе рассматриваются три вида поставщиков: поставщики данных, поставщиков служб и компонентов службы. Поставщики делятся на две категории: те, предоставляющая данные и их предоставления служб. Объект *поставщик данных* владеет собственными данными и передают их в табличную форму в приложение. Объект *поставщика услуг* инкапсулирует службы, создавая и используя данные, дополнение функции в приложениях ADO. Поставщик услуг может также быть указан как *компонент службы*, который должны работать вместе с других поставщиков служб или компонентов.

## <a name="data-providers"></a>Поставщики данных
 ADO — мощная и гибкая, так как он может подключиться к любому из нескольких разных поставщиков данных и по-прежнему предоставлять ту же модель программирования, независимо от конкретных функциях любого данного поставщика.

 Тем не менее поскольку каждый поставщик данных является уникальным, как приложение взаимодействует с ADO будет несколько отличаться поставщиком данных. Различия обычно делятся на три категории:

-   Параметры подключения в [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство.

-   [Команда](../../../ado/reference/ado-api/command-object-ado.md) объекта использования.

-   Поставщика [записей](../../../ado/reference/ado-api/recordset-object-ado.md) поведение.

 Подробные сведения для каждого из поставщиков данных, в настоящее время корпорации Microsoft, перечислены ниже.

|Область|Раздел|
|----------|-----------|
|Баз данных ODBC|[Поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Службе индексирования|[Поставщик Microsoft OLE DB для службы индексирования Microsoft](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Службы Active Directory|[Поставщик Microsoft OLE DB для службы Microsoft Active Directory](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Базы данных Microsoft Jet|[Поставщик OLE DB для Jet (Майкрософт)](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Поставщик Microsoft OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|базы данных Oracle;|[Поставщик Microsoft OLE DB для Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|Публикации в Интернете|[Поставщик Microsoft OLE DB для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|Источники данных|[Простой поставщик Microsoft OLE DB](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>Динамические свойства от поставщика
 [Свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [команда](../../../ado/reference/ado-api/command-object-ado.md), и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекты включают динамические свойства, относящиеся к Поставщик. Эти свойства предоставляют сведения о конкретных функциях к поставщику за пределы встроенные свойства, которые поддерживает ADO.

 После установки подключения и создания этих объектов, используйте [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод **свойства** коллекцию объекта, чтобы получить свойства от поставщика. См. в документации по поставщику и [Руководство программиста OLE DB](http://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) подробные сведения о динамических свойствах.

## <a name="service-providers"></a>Поставщики услуг
 Чтобы использовать поставщик службы, необходимо указать ключевое слово. Также следует учитывать динамические свойства от поставщика, связанный с каждым поставщиком услуг. Сведения поставщика, приведены для каждого поставщика службы, доступной от корпорации Майкрософт:

-   [Служба формирования данных для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Поставщик Microsoft OLE DB сохраняемости](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Поставщик Microsoft OLE DB удаленного взаимодействия](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>Компоненты службы
 [Служба курсора для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) компонент службы дополняет поддержки курсорных функций какого поставщиков данных. Он также требует ключевое слово и динамические свойства.

 Дополнительные сведения о поставщиках OLE DB см. в разделе [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx).

## <a name="provider-commands"></a>Команды поставщика
 Для каждого поставщика в списке, если приложения позволяют пользователям вводить инструкции SQL, как команды поставщика, необходимо всегда проверять вводимые пользователем данные и быть бдительными злоумышленник возможных атак с помощью потенциально опасных инструкций SQL, таких как `DROP TABLE t1`, как часть вводимых пользователем данных.

## <a name="see-also"></a>См. также
 [Команда объект (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [поставщик Microsoft OLE DB для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) [поставщик Microsoft OLE DB для службы Microsoft Active Directory ](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [Поставщик Microsoft OLE DB для службы индексирования Microsoft](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md) [поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [поставщик Microsoft OLE DB для Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) [Поставщик Microsoft OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) [поставщик Microsoft OLE DB для Jet (Майкрософт)](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [ Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [обновить метод (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
