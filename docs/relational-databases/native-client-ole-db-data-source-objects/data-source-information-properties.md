---
title: Сведения о свойства источника данных | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 09f0c3c80bf2ab689cab3f399fb3a50535248704
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-source-information-properties"></a>Свойства сведений об источнике данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERDATASOURCEINFO поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет следующие свойства, хранящие информацию об источнике данных.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Тип: VT_BOOL<br /><br /> Чтение R Чтение и запись:<br /><br /> По умолчанию: значение VARIANT_TRUE<br /><br /> Описание: Используется для определения, поддерживается ли параметры сортировки столбца.<br /><br /> VARIANT_TRUE: Поддерживаемые параметры сортировки уровня столбцов.<br /><br /> VARIANT_FALSE: Параметры сортировки уровня столбцов не поддерживается.|  
|SSPROP_UNICODELCID|Тип: VT_I4 R Чтение и запись: чтение<br /><br /> Описание: Юникод, идентификатор языка.<br /><br /> Это локаль, используемый для сортировки данных в Юникоде.|  
|SSPROP_UNICODECOMPARISONSTYLE|Тип: VT_I4 R Чтение и запись: чтение<br /><br /> Описание: Стиль сравнения Юникод.<br /><br /> Параметры сортировки, используемые для сортировки данных в Юникоде.|  
  
 В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERSTREAM поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет следующее дополнительное свойство.  
  
|Идентификатор свойства|Описание|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Тип: VT_BSTR R Чтение и запись: чтение и запись<br /><br /> Описание: Результат запроса FOR XML не может быть документом правильного формата. Если это свойство задано, результат "выберите... FOR XML "запрос упаковывается в корневом теге, предоставляемые этим свойством, для возвращения документа XML с правильным форматом. Если запрос выполняется в браузере, при загрузке результата в окне браузера может быть выведена информация об ошибках средства синтаксического анализа. Для избежания этой ошибки в SQL ISAPI применяется ключевое слово ROOT. Оно соответствует свойству SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>См. также  
 [Объекты источника данных & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
