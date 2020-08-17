---
description: IMPORT (расширения интеллектуального анализа данных)
title: IMPORT (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5da00163792b18bfd62ed0db4be0945f358115e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88352690"
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
  
## <a name="remarks"></a>Remarks  
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
  
  
