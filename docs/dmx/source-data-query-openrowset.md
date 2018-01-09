---
title: "OPENROWSET (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: OPENROWSET
dev_langs: DMX
helpviewer_keywords: OPENROWSET statement
ms.assetid: 8c8b61b4-2bf6-46c7-8976-51484004dc22
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2a3a7f8e9cbfcb6791cee28bb412be0ff51fc5df
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;запрос источника данных&gt; -OPENROWSET
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Remarks  
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
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
