---
title: Типы данных SQL Server и ADO.NET
description: Описание работы с типами данных SQL Server и способов их взаимодействия с типами данных .NET.
ms.date: 08/15/2019
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 46edb611f29c447f7e1ca2228212ef3e0d594fff
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244044"
---
# <a name="sql-server-data-types-and-adonet"></a>Типы данных SQL Server и ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server и .NET основаны на разных типах систем, что может привести к потере данных. Чтобы сохранить целостность данных, поставщик данных Microsoft SqlClient для SQL Server (<xref:Microsoft.Data.SqlClient>) предоставляет типизированные методы доступа для работы с данными SQL Server. Перечисления в классах <xref:System.Data.SqlDbType> можно использовать для указания типов данных <xref:Microsoft.Data.SqlClient.SqlParameter>.  
  
В SQL Server 2008 появились новые типы данных, разработанные для удовлетворения бизнес-потребностей при работе с датами и временем, структурированными, частично структурированными и неструктурированными данными. Они описаны в электронной документации на SQL Server 2008.  
  
Типы данных SQL Server, доступные для использования в приложении, зависят от используемой версии SQL Server. Дополнительные сведения см. в разделе [Типы данных (компонент Database Engine)](https://go.microsoft.com/fwlink/?LinkID=107468) в электронной документации по SQL Server.
  
## <a name="in-this-section"></a>В этом разделе  
[Типы SqlType и набор данных](sqltypes-dataset.md)  
Описывает тип поддержки пространства имен `SqlTypes` в `DataSet`.  
  
[Обработка значений NULL](handle-null-values.md)  
Демонстрирует работу со значениями NULL и логикой трех значений.  
  
[Сравнение значений идентификатора GUID и uniqueidentifier](compare-guid-uniqueidentifier-values.md)  
Здесь демонстрируется работа со значениями идентификатора GUID и uniqueidentifier в SQL Server и .NET.  
  
[Данные даты и времени](date-time-data.md)  
В этой статье описывается использование новых типов данных даты и времени, появившихся в SQL Server 2008.  
  
[Большие UDT](large-udts.md)  
Здесь демонстрируется получение данных из UDT с большими значениями, представленных в SQL Server 2008.  
  
[Данные XML в SQL Server](xml-data-sql-server.md)  
Сведения о том, как работать с XML-данными, полученными из SQL Server.  
  
## <a name="reference"></a>Справочник  
<xref:System.Data.DataSet>  
Описание класса `DataSet` и всех его членов.  
  
<xref:System.Data.SqlTypes>  
Описание пространства имен `SqlTypes` и всех его членов.  
  
<xref:System.Data.SqlDbType>  
Описание перечисления `SqlDbType` и всех его членов.  
  
<xref:System.Data.DbType>  
Описание перечисления `DbType` и всех его членов.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Параметры, возвращающие табличные значения](table-valued-parameters.md)
- [Двоичные данные и данные больших значений SQL Server](sql-server-binary-large-value-data.md)
