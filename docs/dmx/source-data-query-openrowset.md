---
title: OPENROWSET (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 125fe829c3b76be0d92a3519249df571890efbf2
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670020"
---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;запрос источника данных &gt; — OPENROWSET
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Заменяет запрос источника данных на запрос к внешнему поставщику. Инструкция INSERT, выбор из ПРОГНОЗИРУЕМого объединения и выбор из операторов ЕСТЕСТВЕННОго ПРОГНОЗИРУЮЩЕГО подключения поддерживают **OPENROWSET**.  
  
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
  
## <a name="remarks"></a>Комментарии  
 Поставщик интеллектуального анализа данных установит соединение с объектом источника данных с помощью *provider_name* и provider_string и будет выполнять запрос *,* указанный в *query_syntax* , для получения набора строк из исходных данных.  
  
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
 [&#62;запроса источника данных&#60;](../dmx/source-data-query.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
