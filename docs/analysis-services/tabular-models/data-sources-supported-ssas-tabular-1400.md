---
title: Поддерживаемые источники данных в SQL Server Analysis Services для табличных моделей 1400 | Документация Майкрософт
ms.date: 02/12/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4c900c6f1683b9f4c96355a759c604022515d2ce
ms.sourcegitcommit: 89a7bd9ccbcb19bb92a1f4ba75576243a58584e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56159759"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Источники данных, поддерживаемые в SQL Server Analysis Services табличных моделей 1400

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

В этой статье описаны типы источников данных, которые могут использоваться с табличными моделями служб SQL Server Analysis Services (SSAS) с уровнем совместимости 1400. 

SSAS табличных моделей на уровне совместимости 1200 и ниже, см. в разделе [поддерживаемые источники данных в SQL Server Analysis Services для табличных моделей 1200](data-sources-supported-ssas-tabular.md).

Службы Azure Analysis Services, см. в разделе [источники данных, поддерживаемые в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Облачными источниками данных

|Источник данных  |В памяти  |DirectQuery  |
|---------|---------|---------|
|База данных SQL Azure     |   Да      |    Да      |
|Хранилище данных SQL Azure     |   Да      |   Да       |
|хранилище BLOB-объектов Azure     |   Да       |    Нет      |
|Хранилище таблиц Azure    |   Да       |    Нет      |
|Azure Cosmos DB     |  Да        |  Нет        |
|Azure Data Lake Store (поколение 1)<sup>[1](#gen2)</sup>      |   Да       |    Нет      |
|Azure HDInsight HDFS    |     Да     |   Нет       |
|Azure HDInsight Spark <sup> [2](#databricks)</sup>     |   Да       |   Нет       |
||||

<a name="gen2">1</a> -ADLS Gen2 сейчас не поддерживается.   
<a name="databricks">2</a> — azure Databricks с помощью Spark, соединитель в настоящее время не поддерживается.   



**Поставщик**   
В памяти и моделей DirectQuery, подключающихся к источникам данных Azure используйте поставщик данных .NET Framework для SQL Server.

## <a name="on-premises-data-sources"></a>Локальные источники данных

### <a name="supported-by-in-memory-and-directquery-models"></a>Поддерживается в памяти и моделей DirectQuery

|Источник данных | Поставщик в памяти | Поставщик DirectQuery |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0, поставщик Microsoft OLE DB для SQL Server, поставщик данных .NET Framework для SQL Server | Поставщик данных .NET Framework для SQL Server |
| Хранилище данных SQL Server |SQL Server Native Client 11.0, поставщик Microsoft OLE DB для SQL Server, поставщик данных .NET Framework для SQL Server | Поставщик данных .NET Framework для SQL Server |
| Oracle; |Поставщик Microsoft OLE DB для Oracle, поставщик данных Oracle для .NET |Поставщик данных Oracle для .NET | |
| Teradata |Поставщик OLE DB для Teradata, поставщик данных Teradata для .NET |Поставщик данных Teradata для .NET | |
| | | |

> [!NOTE]
> Для моделей в памяти поставщики OLE DB можно обеспечить лучшую производительность для больших объемов данных. При выборе между разными поставщиками, для одного источника данных, сначала поставщик OLE DB.  

### <a name="supported-by-in-memory-models-only"></a>Поддерживается только в моделях в памяти

|База данных  |
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
|Книга Excel     |
|Папка     | 
|JSON | 
|Text/CSV    | 
|XML-таблицы    | 
|||

|Веб-служб  |  
|---------|---------|
|Dynamics 365      |
|Популяризацию через Интернет     |
|Объекты Saleforce    | 
|Отчеты SalesForce     |
|Список SharePoint Online     |
|||

|Другое  |  
|---------|---------|
|Active Directory      | 
|Популяризацию     |  
|Веб-канал OData     | 
|Запрос ODBC     | 
|OLE DB  | 
|Список SharePoint | 
|||

## <a name="see-also"></a>См. также

[Источники данных, поддерживаемые в SQL Server Analysis Services табличных моделей 1200](data-sources-supported-ssas-tabular.md)

[Поддерживаемые источники данных в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
