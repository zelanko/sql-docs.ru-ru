---
title: Источники данных, поддерживаемые в SQL Server Analysis Services табличной модели 1400 | Документы Microsoft
ms.date: 03/26/2018
ms.prod: analysis-services
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: ''
author: Minewiskan
ms.author: owend
manager: kfile
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 7f2ae9498b0d177234fd75bb0de9ea0b61d15746
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Источники данных поддерживается в SQL Server Analysis Services табличной модели 1400

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

В этой статье описываются типы источников данных, которые можно использовать с табличными моделями служб SQL Server Analysis Services (SSAS) на уровне совместимости 1400. 

SSAS табличных моделей на уровне совместимости 1200 и ниже, в разделе [источники данных, поддерживаемые в SQL Server Analysis Services табличной модели 1200](data-sources-supported-ssas-tabular.md).

Azure Analysis Services. в разделе [источники данных, поддерживаемые в службах Analysis Services Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Источники данных в облаке

|Источник данных Azure  |В памяти  |DirectQuery  |
|---------|---------|---------|
|Azure SQL Database     |   Да      |    Да      |
|Хранилище данных SQL Azure     |   Да      |   Да       |
|хранилище BLOB-объектов Azure.     |   Да       |    Нет      |
|Хранилище таблиц Azure    |   Да       |    Нет      |
|DB Azure Cosmos      |  Да        |  Нет        |
|Хранилище Озера данных Azure     |   Да       |    Нет      |
|Azure HDInsight HDFS     |     Да     |   Нет       |
|Azure HDInsight Spark (бета-версия)     |   Да       |   Нет       |
||||

**Поставщик**   
В памяти и моделей DirectQuery соединения с источниками данных Azure используйте поставщик данных .NET Framework для SQL Server.

## <a name="on-premises-data-sources"></a>Локальные источники данных

### <a name="supported-by-in-memory-and-directquery-models"></a>Поддерживается в памяти и моделей DirectQuery

|Источник данных | Поставщик в памяти | Поставщик DirectQuery |
|  --- | --- | --- |
| SQL Server |Собственный клиент SQL Server 11.0 поставщик Microsoft OLE DB для SQL Server, поставщик данных .NET Framework для SQL Server | Поставщик данных .NET Framework для SQL Server |
| Хранилище данных SQL Server |Собственный клиент SQL Server 11.0 поставщик Microsoft OLE DB для SQL Server, поставщик данных .NET Framework для SQL Server | Поставщик данных .NET Framework для SQL Server |
| Oracle; |Поставщик Microsoft OLE DB для Oracle, поставщик данных Oracle для .NET |Поставщик данных Oracle для .NET | |
| Teradata |Поставщик OLE DB для Teradata, поставщик данных Teradata для .NET |Поставщик данных Teradata для .NET | |
| | | |

> [!NOTE]
> Для моделей в памяти поставщики OLE DB можно обеспечить более высокую производительность для крупномасштабных данных. При выборе между разными поставщиками для одного источника данных, начните с поставщика OLE DB.  

### <a name="supported-by-in-memory-models-only"></a>Поддерживается только в моделях в памяти

|база данных  |
|---------|---------|---------|
|База данных Access     | 
|службы SQL Server Analysis Services     | 
|IBM Informix (бета-версия) | 
|Документ JSON     | 
|Строки из двоичного файла     | 
|База данных MySQL     | 
|База данных PostgreSQL    | Да | Нет
|SAP HANA   | Да | Нет
|SAP Business Warehouse    | Да | Нет
|База данных Sybase     | Да | Нет
|||

|Файл  |  
|---------|---------|
|Книги Excel     |
|Папка     | 
|JSON | 
|Text/CSV    | 
|XML-таблицы    | 
|||

|Интернет-служб  |  
|---------|---------|
|Dynamics 365      |
|Них поддержку через Интернет     |
|Объекты Saleforce    | 
|Отчеты SalesForce     |
|Список SharePoint Online     |
|||

|Другое  |  
|---------|---------|
|Active Directory      | 
|Них поддержку     |  
|Веб-канал OData     | 
|Запрос ODBC     | 
|OLE DB  | 
|Список SharePoint | 
|||

## <a name="see-also"></a>См. также:

[Источники данных, поддерживаемые в SQL Server Analysis Services табличных моделей 1200](data-sources-supported-ssas-tabular.md)

[Источники данных, поддерживаемые в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
