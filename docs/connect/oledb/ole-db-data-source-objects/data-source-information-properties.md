---
title: Свойства сведений об источнике данных (драйвер OLE DB) | Документация Майкрософт
description: Узнайте о свойствах сведений в источнике данных в специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERDATASOURCEINFO в OLE DB Driver for SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 866d4edb2aaece799a25f5f95d176b3702cbb476
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862436"
---
# <a name="data-source-information-properties"></a>Свойства сведений об источнике данных
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERDATASOURCEINFO драйвер OLE DB для SQL Server определяет указанные ниже свойства, хранящие информацию об источнике данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Тип: VT_BOOL.<br /><br /> Ч/З Чтение<br /><br /> Значение по умолчанию: VARIANT_TRUE<br /><br /> Описание. Указывает, поддерживаются ли параметры сортировки столбцов.<br /><br /> VARIANT_TRUE: параметры сортировки на уровне столбцов не поддерживаются.<br /><br /> VARIANT_FALSE: параметры сортировки на уровне столбцов не поддерживаются.|  
|SSPROP_UNICODELCID|Тип: VT_I4 R/W: Чтение<br /><br /> Описание. код локали в Юникоде.<br /><br /> Это локаль, используемый для сортировки данных в Юникоде.|  
|SSPROP_UNICODECOMPARISONSTYLE|Тип: VT_I4 R/W: Чтение<br /><br /> Описание. стиль сравнения Юникод.<br /><br /> Параметры сортировки, используемые для сортировки данных в Юникоде.|  
  
 В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERSTREAM драйвер OLE DB для SQL Server определяет указанное ниже дополнительное свойство.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Тип: VT_BSTR R/W: Чтение/запись<br /><br /> Описание. результат запроса FOR XML может не быть правильно сформированным XML-документом. Если это свойство задано, результат инструкции "select … for XML" окажется завернут в корневой тег, предоставленный данным свойством, для возвращения правильно сформированного XML-документа. Если запрос выполняется в браузере, при загрузке результата в окне браузера может быть выведена информация об ошибках средства синтаксического анализа. Для избежания этой ошибки в SQL ISAPI применяется ключевое слово ROOT. Оно соответствует свойству SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>См. также:  
 [Объекты источников данных (OLE DB)](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
