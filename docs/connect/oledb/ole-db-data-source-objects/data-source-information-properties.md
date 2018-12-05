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
ms.openlocfilehash: 328a8c247fda6d67d40426cfa0f36ac47f686f11
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516684"
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
|SSPROP_STREAM_XMLROOT|Тип: VT_BSTR и запись: чтение и запись<br /><br /> Описание: результат запроса FOR XML может не быть правильно сформированным документом. Если это свойство задано, результат инструкции "select … for XML" окажется завернут в корневой тег, предоставленный данным свойством, для возвращения правильно сформированного XML-документа. Если запрос выполняется в браузере, при загрузке результата в окне браузера может быть выведена информация об ошибках средства синтаксического анализа. Для избежания этой ошибки в SQL ISAPI применяется ключевое слово ROOT. Оно соответствует свойству SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>См. также:  
 [Объекты источника данных &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
