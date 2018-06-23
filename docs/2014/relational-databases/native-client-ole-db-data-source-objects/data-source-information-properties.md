---
title: Сведения о свойства источника данных | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 980e7ea889cc8c95828b4c704748aa6dc2552359
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190433"
---
# <a name="data-source-information-properties"></a>Свойства сведений об источнике данных
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
 [Объекты источников данных &#40;OLE DB&#41;](data-source-objects-ole-db.md)  
  
  