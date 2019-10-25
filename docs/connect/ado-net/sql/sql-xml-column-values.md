---
title: Значения столбцов XML SQL
description: Демонстрация получения и работы с XML-данными, полученными из SQL Server.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d8dc9d5100f71fed39c1e4166882230451dd139e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451937"
---
# <a name="sql-xml-column-values"></a>Значения столбцов XML SQL

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

В SQL Server поддерживается тип данных `xml`, поэтому разработчики могут получать результирующие наборы с данными этого типа с помощью стандартных средств класса <xref:Microsoft.Data.SqlClient.SqlCommand>. Столбец `xml` может быть извлечен при извлечении любого столбца (например, в <xref:Microsoft.Data.SqlClient.SqlDataReader>), но если требуется работать с содержимым столбца в формате XML, необходимо использовать <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Пример  
В следующем приложении командной строки в экземпляр <xref:Microsoft.Data.SqlClient.SqlDataReader> выбираются две строки, каждая из которых содержит столбец `xml`, из таблицы **Sales.Store** базы данных **AdventureWorks**. Для каждой строки значение столбца `xml` считывается с помощью метода <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> <xref:Microsoft.Data.SqlClient.SqlDataReader>. Значение хранится в <xref:System.Xml.XmlReader>. Обратите внимание, что для установки содержимого в переменную <xref:System.Data.SqlTypes.SqlXml> необходимо использовать <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A>, а не метод <xref:System.Data.IDataRecord.GetValue%2A>.  <xref:System.Data.IDataRecord.GetValue%2A> возвращает значение столбца `xml` в виде строки.  
  
> [!NOTE]
>  Образец базы данных **AdventureWorks** не устанавливается по умолчанию при установке SQL Server. Его можно установить, запустив программу установки SQL Server.  
  
[!code-csharp[DataWorks SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>Дальнейшие действия
- <xref:System.Data.SqlTypes.SqlXml>
- [Данные XML в SQL Server](xml-data-sql-server.md)
