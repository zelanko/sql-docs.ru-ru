---
title: IMPORT (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1bddae4cf71b30a2a1365d0d5748170c0d5bac53
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86969829"
---
# <a name="import-dmx"></a>IMPORT (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Загружает модель или структуру интеллектуального анализа данных из файла резервной копии служб Analysis Services (ABF) на сервер.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>Аргументы  
 *filename*  
 Строка с именем и расположением файла для импорта.  
  
## <a name="remarks"></a>Примечания  
 Если объекты не указаны, то загружается все содержимое DMB-файла. Если в DMB-файле содержится ссылка на несуществующую на сервере базу данных, то указанная база данных будет создана.  
  
 Только администратор базы данных или сервера имеет право экспортировать и импортировать объекты.  
  
## <a name="import-from-file-example"></a>Импорт из образца файла  
 В следующем примере выполняется импорт всего содержимого файла с моделью взаимосвязей и структурой на текущий сервер.  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41; DDL](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)   
 [ЭКСПОРТ &#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&#41;](../dmx/export-dmx.md)   
 [Экспорт и импорт объектов интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
  
