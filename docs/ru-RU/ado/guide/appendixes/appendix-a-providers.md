---
title: Приложение а. поставщики | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f367b244755837595fc1357d8a1824e4f7fa30b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="appendix-a-data-and-service-providers"></a>Приложение a. данных и поставщики услуг
В этом разделе описываются три вида поставщики: поставщики данных, поставщиков услуг и службы компонентов. Поставщики делятся на две категории: те, предоставление данных, так и предоставления услуг. Объект *поставщик данных* владеет собственными данными и предоставляет доступ к нему в табличной форме в приложении. Объект *поставщика услуг* инкапсулирует службы, создания и использования данных, расширения возможностей в приложениях ADO. Поставщик услуг может также детализировать как *компонент службы*, которой должны работать вместе с другой поставщик службы или компоненты.

## <a name="data-providers"></a>Поставщики данных
 ADO — мощная и гибкая, так как он может подключиться к одному из нескольких разных поставщиков данных и по-прежнему предоставляют такую же модель программирования, независимо от конкретных функциях любой заданный поставщик.

 Однако каждый поставщик данных является уникальным, как приложение взаимодействует с ADO могут различаться немного поставщиком данных. Различия обычно делятся на три категории:

-   Параметры подключения в [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство.

-   [Команда](../../../ado/reference/ado-api/command-object-ado.md) объекта использования.

-   Специфический для поставщика [записей](../../../ado/reference/ado-api/recordset-object-ado.md) поведение.

 Ниже представлены сведения для каждого из поставщиков данных, доступных в настоящее время корпорации Майкрософт.

|Область|Раздел|
|----------|-----------|
|Баз данных ODBC|[Поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)|
|Службе индексирования|[Поставщик Microsoft OLE DB для службы индексирования Microsoft](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Службы Active Directory|[Поставщик Microsoft OLE DB для службы Microsoft Active Directory](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Базы данных Microsoft Jet|[Поставщик OLE DB для Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Поставщик Microsoft OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)|
|базы данных Oracle;|[Поставщик Microsoft OLE DB для Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)|
|Публикация в Интернете|[Поставщик Microsoft OLE DB для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)|
|К источникам простых данных|[Простой поставщик Microsoft OLE DB](../../../ado/guide/appendixes/microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>Динамические свойства от поставщика
 [Свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции [подключения](../../../ado/reference/ado-api/connection-object-ado.md), [команда](../../../ado/reference/ado-api/command-object-ado.md), и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекты включают динамические свойства, относящиеся к Поставщик. Эти свойства предоставляют сведения о конкретных функциях к поставщику за пределами встроенные свойства, которые поддерживает ADO.

 После установления соединения и создания этих объектов, используйте [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод **свойства** коллекцию объекта, чтобы получить свойства от поставщика. Обратитесь к документации поставщика и [Руководство программиста OLE DB](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) подробные сведения о динамических свойствах.

## <a name="service-providers"></a>Поставщики услуг
 Чтобы использовать поставщик услуг, необходимо указать ключевое слово. Также следует учитывать поставщика динамические свойства, связанные с каждым поставщиком услуг. Для каждого поставщика службы, который в настоящее время доступно представлены сведения от поставщика:

-   [Служба формирования данных для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Поставщик Microsoft OLE DB сохраняемости](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Поставщик Microsoft OLE DB удаленного взаимодействия](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>Службы компонентов
 [Служба курсора для OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) компонент службы дополняют поддержки курсорных функций поставщиков данных. Он также требуется ключевое слово и имеет динамических свойств.

 Дополнительные сведения о поставщиках OLE DB см. в разделе [Microsoft OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx).

## <a name="provider-commands"></a>Команды поставщика
 Для каждого поставщика в этом списке, если приложения позволяют пользователям вводить инструкции SQL как команды поставщика, необходимо всегда проверки пользовательского ввода и будьте бдительны злоумышленнику возможных атак с помощью потенциально опасных инструкций SQL, таких как `DROP TABLE t1`, в рамках пользовательского ввода.

## <a name="see-also"></a>См. также
 [Команды объекта (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [поставщик Microsoft OLE DB для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md) [поставщик Microsoft OLE DB для службы Microsoft Active Directory ](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-active-directory-service.md) [Поставщик Microsoft OLE DB для службы индексирования Microsoft](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-indexing-service.md) [поставщик Microsoft OLE DB для ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md) [поставщик Microsoft OLE DB для Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) [Поставщик Microsoft OLE DB для SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) [поставщик Microsoft OLE DB для Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) [коллекции свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [ Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [обновить метод (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
