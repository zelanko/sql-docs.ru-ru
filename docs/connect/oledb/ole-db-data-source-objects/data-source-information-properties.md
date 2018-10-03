---
title: Сведения свойства источника данных | Документация Майкрософт
description: Свойства сведений об источнике данных
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
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: ab8c77e44c5ed8646e3ffb1f80718d618c234b39
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600171"
---
# <a name="data-source-information-properties"></a>Свойства сведений об источнике данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERDATASOURCEINFO драйвер OLE DB для SQL Server определяет указанные ниже свойства, хранящие информацию об источнике данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Тип: VT_BOOL<br /><br /> Чтение и запись:<br /><br /> По умолчанию: значение VARIANT_TRUE<br /><br /> Описание: указывает, поддерживаются ли параметры сортировки столбцов.<br /><br /> VARIANT_TRUE: Поддерживаемые параметры сортировки на уровне столбца.<br /><br /> VARIANT_FALSE: Параметры сортировки уровня столбцов не поддерживается.|  
|SSPROP_UNICODELCID|Тип: Чтение и запись: VT_I4<br /><br /> Описание: Юникод, идентификатор языка.<br /><br /> Это локаль, используемый для сортировки данных в Юникоде.|  
|SSPROP_UNICODECOMPARISONSTYLE|Тип: Чтение и запись: VT_I4<br /><br /> Описание: Стиль сравнения Юникод.<br /><br /> Параметры сортировки, используемые для сортировки данных в Юникоде.|  
  
 В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERSTREAM драйвер OLE DB для SQL Server определяет указанное ниже дополнительное свойство.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Тип: VT_BSTR и запись: чтение и запись<br /><br /> Описание: результат запроса FOR XML может не быть правильно сформированным документом. Если это свойство задано, результат "выберите... для XML "запрос упаковывается в корневой тег, предоставленный данным свойством, для возврата правильного формата XML-документа. Если запрос выполняется в браузере, при загрузке результата в окне браузера может быть выведена информация об ошибках средства синтаксического анализа. Для избежания этой ошибки в SQL ISAPI применяется ключевое слово ROOT. Оно соответствует свойству SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>См. также:  
 [Объекты источника данных &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
