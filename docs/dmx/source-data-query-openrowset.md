---
title: "OPENROWSET (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENROWSET
dev_langs:
- DMX
helpviewer_keywords:
- OPENROWSET statement
ms.assetid: 8c8b61b4-2bf6-46c7-8976-51484004dc22
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 914e1be70255414373fd758301ef0682f3aba6e7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;запрос источника данных&gt; -OPENROWSET
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Заменяет запрос источника данных на запрос к внешнему поставщику. Инструкции INSERT, SELECT FROM PREDICTION JOIN и SELECT FROM NATURAL PREDICTION JOIN поддерживают **OPENROWSET**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OPENROWSET(provider_name,provider_string,query_syntax)  
```  
  
## <a name="arguments"></a>Аргументы  
 *provider_name*  
 Имя поставщика OLE DB.  
  
 *provider_string*  
 Строка подключения OLE DB для определенного поставщика.  
  
 *query_syntax*  
 Синтаксис запроса, возвращающего набор строк.  
  
## <a name="remarks"></a>Замечания  
 Поставщик интеллектуального анализа данных установит соединение с источником данных с помощью *provider_name* и *provider_string,* и выполнит запрос, указанный в *query_syntax* для извлечения набора строк из источника данных.  
  
## <a name="examples"></a>Примеры  
 Следующий пример можно использовать внутри инструкции PREDICTION JOIN для получения данных от базы данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] с помощью инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT.  
  
```  
OPENROWSET  
(  
'SQLOLEDB.1',  
'Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security     Info=False;Initial Catalog=AdventureWorksDW2012;Data Source=localhost',  
'SELECT TOP 1000 * FROM vTargetMail'  
)  
```  
  
## <a name="see-also"></a>См. также:  
 [&#60; запросом источника данных &#62;](../dmx/source-data-query.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

