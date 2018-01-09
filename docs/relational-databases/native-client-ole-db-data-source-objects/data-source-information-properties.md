---
title: "Сведения о свойства источника данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 19d31d68f22aa9ac29c57a04ce0c8d1d7af28bbc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="data-source-information-properties"></a>Свойства сведений об источнике данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERDATASOURCEINFO поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет следующие свойства, хранящие информацию об источнике данных.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Тип: VT_BOOL<br /><br /> Чтение R Чтение и запись:<br /><br /> По умолчанию: значение VARIANT_TRUE<br /><br /> Описание: Используется для определения, поддерживается ли параметры сортировки столбца.<br /><br /> VARIANT_TRUE: Поддерживаемые параметры сортировки уровня столбцов.<br /><br /> VARIANT_FALSE: Параметры сортировки уровня столбцов не поддерживается.|  
|SSPROP_UNICODELCID|Тип: VT_I4 R Чтение и запись: чтение<br /><br /> Описание: Юникод, идентификатор языка.<br /><br /> Это локаль, используемый для сортировки данных в Юникоде.|  
|SSPROP_UNICODECOMPARISONSTYLE|Тип: VT_I4 R Чтение и запись: чтение<br /><br /> Описание: Стиль сравнения Юникод.<br /><br /> Параметры сортировки, используемые для сортировки данных в Юникоде.|  
  
 В специфичном для каждого поставщика множестве свойств DBPROPSET_SQLSERVERSTREAM поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет следующее дополнительное свойство.  
  
|Идентификатор свойства|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Тип: VT_BSTR R Чтение и запись: чтение и запись<br /><br /> Описание: Результат запроса FOR XML не может быть документом правильного формата. Если это свойство задано, результат "выберите... FOR XML "запрос упаковывается в корневом теге, предоставляемые этим свойством, для возвращения документа XML с правильным форматом. Если запрос выполняется в браузере, при загрузке результата в окне браузера может быть выведена информация об ошибках средства синтаксического анализа. Для избежания этой ошибки в SQL ISAPI применяется ключевое слово ROOT. Оно соответствует свойству SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>См. также:  
 [Объекты источника данных &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
