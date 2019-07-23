---
title: Свойства сведений об источнике данных | Документация Майкрософт
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
ms.openlocfilehash: ba9fa21f0c22c342922946a43124216a25ba09ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016032"
---
# <a name="data-source-information-properties"></a>Свойства сведений об источнике данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERDATASOURCEINFO драйвер OLE DB для SQL Server определяет указанные ниже свойства, хранящие информацию об источнике данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Тип: VT_BOOL<br /><br /> Чтение и запись.<br /><br /> По умолчанию: VARIANT_TRUE<br /><br /> Описание: указывает, поддерживаются ли параметры сортировки столбцов.<br /><br /> VARIANT_TRUE: параметры сортировки на уровне столбцов поддерживаются.<br /><br /> VARIANT_FALSE: параметры сортировки на уровне столбцов не поддерживаются.|  
|SSPROP_UNICODELCID|Тип: VT_I4 R/W: Read<br /><br /> Описание: идентификатор языка Юникода.<br /><br /> Это локаль, используемый для сортировки данных в Юникоде.|  
|SSPROP_UNICODECOMPARISONSTYLE|Тип: VT_I4 R/W: Read<br /><br /> Описание: стиль сравнения Юникода.<br /><br /> Параметры сортировки, используемые для сортировки данных в Юникоде.|  
  
 В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERSTREAM драйвер OLE DB для SQL Server определяет указанное ниже дополнительное свойство.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Тип: VT_BSTR R/W: чтение и запись<br /><br /> Описание: результат запроса FOR XML может не быть правильно сформированным документом. Если это свойство задано, результат инструкции "select … for XML" окажется завернут в корневой тег, предоставленный данным свойством, для возвращения правильно сформированного XML-документа. Если запрос выполняется в браузере, при загрузке результата в окне браузера может быть выведена информация об ошибках средства синтаксического анализа. Для избежания этой ошибки в SQL ISAPI применяется ключевое слово ROOT. Оно соответствует свойству SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40;источника данных OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
