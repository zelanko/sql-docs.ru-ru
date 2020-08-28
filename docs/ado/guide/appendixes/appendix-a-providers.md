---
description: Приложение а. поставщики данных и служб
title: Приложение а. поставщики | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- providers [ADO]
- ADO, providers
- service providers [ADO]
- service components [ADO]
ms.assetid: e2581b47-b11e-4e1e-b96c-d39c77c5b48a
author: rothja
ms.author: jroth
ms.openlocfilehash: d50f77959b21031b03ae9591181c61a3419577fd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991175"
---
# <a name="appendix-a-data-and-service-providers"></a>Приложение а. поставщики данных и служб
В этом разделе рассматриваются три типа поставщиков: поставщики данных, поставщики услуг и компоненты службы. Поставщики делятся на две категории: они предоставляют данные и предоставляют службы. *Поставщик данных* владеет собственными данными и предоставляет его в табличном виде в приложение. *Поставщик услуг* инкапсулирует службу, создавая и используя данные, расширяя функции в приложениях ADO. Поставщик услуг также может быть дополнительно определен как *компонент службы*, который должен работать вместе с другими поставщиками услуг или компонентами.

## <a name="data-providers"></a>Поставщики данных
 ADO является мощным и гибким средством, поскольку может подключаться к любому из нескольких разных поставщиков данных и по-прежнему предоставлять ту же модель программирования независимо от конкретных функций любого поставщика.

 Однако, поскольку каждый поставщик данных является уникальным, то, как ваше приложение взаимодействует с ADO, может немного отличаться поставщиком данных. Различия обычно относятся к одной из трех категорий:

-   Параметры соединения в свойстве [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) .

-   Использование объекта [команды](../../reference/ado-api/command-object-ado.md) .

-   Поведение [набора записей](../../reference/ado-api/recordset-object-ado.md) , зависящее от поставщика.

 Сведения для каждого из поставщиков данных, доступных в настоящее время в корпорации Майкрософт, перечислены ниже.

|Область|Раздел|
|----------|-----------|
|Базы данных ODBC|[Поставщик Microsoft OLE DB для ODBC](./microsoft-ole-db-provider-for-odbc.md)|
|Служба индексирования (Майкрософт)|[Поставщик OLE DB для службы индексирования Microsoft (Microsoft)](./microsoft-ole-db-provider-for-microsoft-indexing-service.md)|
|Служба Active Directory|[Поставщик OLE DB Майкрософт для службы Microsoft Active Directory](./microsoft-ole-db-provider-for-microsoft-active-directory-service.md)|
|Базы данных Microsoft Jet|[Поставщик OLE DB для Microsoft Jet](./microsoft-ole-db-provider-for-microsoft-jet.md)|
|Microsoft SQL Server|[Поставщик Microsoft OLE DB для SQL Server](./microsoft-ole-db-provider-for-sql-server.md)|
|базы данных Oracle;|[Поставщик OLE DB для Oracle (Microsoft)](./microsoft-ole-db-provider-for-oracle.md)|
|Публикация в Интернете|[Поставщик OLE DB Майкрософт для публикации в Интернете](./microsoft-ole-db-provider-for-internet-publishing.md)|
|Простые источники данных|[Простой поставщик Microsoft OLE DB](./microsoft-ole-db-simple-provider.md)|

## <a name="provider-specific-dynamic-properties"></a>Динамические свойства, зависящие от поставщика
 Коллекции [свойств](../../reference/ado-api/properties-collection-ado.md) объектов [соединения](../../reference/ado-api/connection-object-ado.md), [команды](../../reference/ado-api/command-object-ado.md)и [набора записей](../../reference/ado-api/recordset-object-ado.md) включают динамические свойства, относящиеся к поставщику. Эти свойства предоставляют сведения о функциях, относящихся к поставщику, за пределами встроенных свойств, поддерживаемых ADO.

 После установления соединения и создания этих объектов используйте метод [Refresh](../../reference/ado-api/refresh-method-ado.md) коллекции **Properties** объекта, чтобы получить свойства, зависящие от поставщика. Подробные сведения об этих динамических свойствах см. в документации поставщика и [OLE DB руководстве программиста](/previous-versions/windows/desktop/ms713643(v=vs.85)) .

## <a name="service-providers"></a>Поставщики услуг
 Для использования поставщика услуг необходимо указать ключевое слово. Кроме того, следует помнить о динамических свойствах конкретного поставщика, связанных с каждым поставщиком служб. Сведения, относящиеся к поставщику, перечислены для каждого поставщика услуг, который в настоящее время доступен корпорации Майкрософт:

-   [Служба формирования данных для OLE DB](./microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)

-   [Поставщик сохраняемости Microsoft OLE DB](./microsoft-ole-db-persistence-provider-ado-service-provider.md)

-   [Поставщик удаленного взаимодействия Microsoft OLE DB](./microsoft-ole-db-remoting-provider-ado-service-provider.md)

## <a name="service-components"></a>Компоненты услуг
 [Служба курсора для компонента OLE DB](./microsoft-cursor-service-for-ole-db-ado-service-component.md) службы дополняет функции поддержки курсоров поставщиками данных. Он также требует ключевого слова и имеет динамические свойства.

 Дополнительные сведения о поставщиках OLE DB см. в разделе [Microsoft OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85)).

## <a name="provider-commands"></a>Команды поставщика
 Для каждого поставщика, указанного здесь, если приложения позволяют пользователям вводить инструкции SQL в качестве команд поставщика, необходимо всегда проверять вводимые пользователем данные и бдительным атаки хакеров с помощью потенциально опасных инструкций SQL, таких как `DROP TABLE t1` , как часть вводимых пользователем данных.

## <a name="see-also"></a>См. также
 [Объект объекта (ADO)](../../reference/ado-api/command-object-ado.md) [Connection Object](../../reference/ado-api/connection-object-ado.md) (ado) [поставщик Microsoft OLE DB для интернет-публикации](./microsoft-ole-db-provider-for-internet-publishing.md) [поставщика Microsoft OLE DB Active Directory для службы](./microsoft-ole-db-provider-for-microsoft-active-directory-service.md) Microsoft [OLE DB](./microsoft-ole-db-provider-for-microsoft-indexing-service.md) поставщик Microsoft OLE DB поставщик Майкрософт для [ODBC](./microsoft-ole-db-provider-for-odbc.md) [поставщик OLE DB для Oracle (Майкрософт)](./microsoft-ole-db-provider-for-oracle.md) Microsoft OLE DB Provider для [SQL Server](./microsoft-ole-db-provider-for-sql-server.md) поставщика Microsoft OLE DB поставщик [Microsoft (ADO](../../reference/ado-api/properties-collection-ado.md) [) (](../../reference/ado-api/recordset-object-ado.md) [RDS) метод обновления](../../reference/rds-api/refresh-method-rds.md) Microsoft [Jet](./microsoft-ole-db-provider-for-microsoft-jet.md)