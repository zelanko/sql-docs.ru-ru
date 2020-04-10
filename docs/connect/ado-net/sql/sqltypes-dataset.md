---
title: Типы SqlType и набор данных
description: Описание поддержки типов SqlTypes в наборе данных.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 2d6f5ec17e800cbac571554a359c2ebd43fa9186
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918574"
---
# <a name="sqltypes-and-the-dataset"></a>Типы SqlType и набор данных

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

В ADO.NET 2.0 добавлена поддержка расширенных типов `DataSet` через пространство имен <xref:System.Data.SqlTypes>. Типы в пространстве имен <xref:System.Data.SqlTypes> предназначены для предоставления типов данных с той же семантикой и точностью, которыми обладают типы данных в базе данных SQL Server. Каждый тип данных в пространстве имен <xref:System.Data.SqlTypes> имеет эквивалентный тип данных в SQL Server с аналогичным базовым представлением данных.  
  
Использование <xref:System.Data.SqlTypes> непосредственно в <xref:System.Data.DataSet> дает несколько преимуществ при работе с типами данных SQL Server. <xref:System.Data.SqlTypes> поддерживает такую же семантику, как и собственные типы данных SQL Server. Указав любой из типов <xref:System.Data.SqlTypes> в определении <xref:System.Data.DataColumn>, вы исключите потерю точности от преобразования типов данных decimal или numeric в типы данных среды CLR.  

В следующем примере создается объект <xref:System.Data.DataTable> с явным определением типов данных <xref:System.Data.DataColumn> при помощи <xref:System.Data.SqlTypes>, а не типов CLR. Этот код заполняет таблицу <xref:System.Data.DataTable> данными из таблицы Sales.SalesOrderDetail базы данных AdventureWorks в SQL Server. Выходные данные, отображаемые в окне консоли, содержат тип данных для каждого столбца и значения, полученные из SQL Server.  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
