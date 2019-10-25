---
title: Типы данных SQL Server и ADO.NET
description: Описание работы с типами данных SQL Server и способов их взаимодействия с типами данных .NET.
ms.date: 08/15/2019
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 12ad13d6788ae2b8995289100883b06c5ab6d7c6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452034"
---
# <a name="sql-server-data-types-and-adonet"></a>Типы данных SQL Server и ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server и .NET основаны на разных системах типов, что может привести к потере данных. Чтобы сохранить целостность данных, поставщик данных Microsoft SqlClient для SQL Server (<xref:Microsoft.Data.SqlClient>) предоставляет типизированные методы доступа для работы с данными SQL Server. Перечисления в классах <xref:System.Data.SqlDbType> можно использовать для указания <xref:Microsoft.Data.SqlClient.SqlParameter> типов данных.  
  
В SQL Server 2008 появились новые типы данных, разработанные для удовлетворения бизнес-потребностей в работе с датами и временем, структурированными, частично структурированными и неструктурированными данными. Они описаны в электронной документации на SQL Server 2008.  
  
SQL Server типы данных, доступные для использования в приложении, зависят от используемой версии SQL Server. Дополнительные сведения см. в разделе [типы данных (ядро СУБД)](https://go.microsoft.com/fwlink/?LinkID=107468) из электронная документация на SQL Server.
  
## <a name="in-this-section"></a>В этом разделе  
[Типы SqlType и набор данных](sqltypes-dataset.md)  
Описывает тип поддержки пространства имен `SqlTypes` в `DataSet`.  
  
[Обработка значений NULL](handle-null-values.md)  
Демонстрирует работу со значениями NULL и логикой с тремя значениями.  
  
[Сравнение значений идентификатора GUID и uniqueidentifier](compare-guid-uniqueidentifier-values.md)  
Демонстрирует работу с GUID и значениями uniqueidentifier в SQL Server и .NET.  
  
[Данные даты и времени](date-time-data.md)  
Описывает, как использовать новые типы данных даты и времени, появившиеся в SQL Server 2008.  
  
[Большие UDT](large-udts.md)  
Демонстрирует получение данных из определяемых пользователем типов больших значений, представленных в SQL Server 2008.  
  
[Данные XML в SQL Server](xml-data-sql-server.md)  
Описывает, как работать с XML-данными, полученными из SQL Server.  
  
## <a name="reference"></a>Справочник  
<xref:System.Data.DataSet>  
Описывает класс `DataSet` и все его члены.  
  
<xref:System.Data.SqlTypes>  
Описывает пространство имен `SqlTypes` и все его члены.  
  
<xref:System.Data.SqlDbType>  
Описывает перечисление `SqlDbType` и все его члены.  
  
<xref:System.Data.DbType>  
Описывает перечисление `DbType` и все его члены.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Параметры, возвращающие табличные значения](table-valued-parameters.md)
- [Двоичные данные и данные больших значений SQL Server](sql-server-binary-large-value-data.md)
