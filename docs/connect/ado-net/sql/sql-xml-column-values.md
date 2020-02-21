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
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: aa02072e139c2446ae67086ef43668af4403890c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244014"
---
# <a name="sql-xml-column-values"></a>Значения столбцов XML SQL

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

В SQL Server поддерживается тип данных `xml`, поэтому разработчики могут получать результирующие наборы с данными этого типа с помощью стандартных средств класса <xref:Microsoft.Data.SqlClient.SqlCommand>. Столбец `xml` может извлекаться как любой другой столбец (например, в <xref:Microsoft.Data.SqlClient.SqlDataReader>), но для работы с содержимым столбца в формате XML необходимо использовать <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Пример  
В следующем приложении командной строки в экземпляр <xref:Microsoft.Data.SqlClient.SqlDataReader> выбираются две строки, каждая из которых содержит столбец `xml`, из таблицы **Sales.Store** базы данных **AdventureWorks**. Для каждой строки значение столбца `xml` считывается с помощью метода <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A> из <xref:Microsoft.Data.SqlClient.SqlDataReader>. Это значение сохраняется в <xref:System.Xml.XmlReader>. Обратите внимание, что для сохранения содержимого в переменную <xref:System.Data.SqlTypes.SqlXml> необходимо использовать метод <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlXml%2A>, а не <xref:System.Data.IDataRecord.GetValue%2A>, так как <xref:System.Data.IDataRecord.GetValue%2A> возвращает значение столбца `xml` в формате строки.  
  
> [!NOTE]
>  Образец базы данных **AdventureWorks** не устанавливается по умолчанию при установке SQL Server. Чтобы установить его, запустите программу установки SQL Server.  
  
[!code-csharp [SqlDataReader_GetSqlXml#1](~/../sqlclient/doc/samples/SqlDataReader_GetSqlXml.cs#1)]
  
## <a name="next-steps"></a>Дальнейшие действия
- <xref:System.Data.SqlTypes.SqlXml>
- [Данные XML в SQL Server](xml-data-sql-server.md)
