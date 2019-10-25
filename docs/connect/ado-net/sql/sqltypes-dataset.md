---
title: Типы SqlType и набор данных
description: Описывает поддержку типов для SqlTypes в наборе данных.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 70efb8615a70677c709abd6d9129c63de9420ffc
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451981"
---
# <a name="sqltypes-and-the-dataset"></a>Типы SqlType и набор данных

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

В ADO.NET 2,0 введена поддержка расширенного типа для `DataSet` через пространство имен <xref:System.Data.SqlTypes>. Типы в <xref:System.Data.SqlTypes> предназначены для предоставления типов данных с той же семантикой и точностью, что и типы данных в базе данных SQL Server. Каждый тип данных в пространстве имен <xref:System.Data.SqlTypes> имеет эквивалентный тип данных в SQL Server с аналогичным базовым представлением данных.  
  
Использование <xref:System.Data.SqlTypes> непосредственно в <xref:System.Data.DataSet> предоставляет несколько преимуществ при работе с типами данных SQL Server. <xref:System.Data.SqlTypes> поддерживает ту же семантику, что и SQL Server собственные типы данных. Указание одного из <xref:System.Data.SqlTypes> в определении <xref:System.Data.DataColumn> исключает потери точности, которая может возникнуть при преобразовании типов данных decimal или numeric в один из типов данных среды CLR.  

В следующем примере создается объект <xref:System.Data.DataTable> с явным определением типов данных <xref:System.Data.DataColumn> при помощи <xref:System.Data.SqlTypes>, а не типов CLR. Этот код заполняет таблицу <xref:System.Data.DataTable> данными из таблицы Sales.SalesOrderDetail базы данных AdventureWorks в SQL Server. Выходные данные, отображаемые в окне консоли, показывают тип данных каждого столбца и значения, полученные из SQL Server.  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
