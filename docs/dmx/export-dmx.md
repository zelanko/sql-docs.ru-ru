---
description: EXPORT (расширения интеллектуального анализа данных)
title: EXPORT (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 689ab632604d26a349dbb3f2a40d5f1b7cf8d702
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88353230"
---
# <a name="export-dmx"></a>EXPORT (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Извлекает модель или объект структуры интеллектуального анализа данных из сервера в файл резервной копии служб Analysis Services (ABF).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Тип объекта*  
 Необязательный параметр. Тип экспортируемого объекта (модель или структура интеллектуального анализа данных).  
  
 *имя объекта*  
 Необязательный параметр. Имя экспортируемого объекта.  
  
 *filename*  
 Имя и расположение файла для экспорта (аргумент типа string).  
  
## <a name="remarks"></a>Remarks  
 Если инструкция указывает модель интеллектуального анализа данных, итоговый файл также содержит связанную структуру интеллектуального анализа данных. Если инструкция указывает **с зависимостями**, все объекты, необходимые для обработки объекта (например, источник данных и представление источника данных), включаются в ABF-файл.  
  
 Для экспорта или импорта объектов из базы данных необходимо быть администратором базы данных или сервера [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="export-mining-structure-example"></a>Пример экспорта структуры интеллектуального анализа данных  
 В следующем примере структуры интеллектуального анализа данных Targeted Mailing и Forecasting, а также модель интеллектуального анализа данных Association экспортируются в определенный файл. Вследствие того, что модель Association является частью структуры интеллектуального анализа Market Basket, в примере также экспортируется структура Market Basket. Любые другие модели интеллектуального анализа данных, которые могут существовать как часть структуры интеллектуального анализа данных для рынка, не будут экспортированы, поскольку модель взаимосвязей была экспортирована с использованием **модели интеллектуального анализа**данных, а не **структуры интеллектуального анализа**  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Пример экспорта модели интеллектуального анализа данных  
 В следующем примере модель интеллектуального анализа данных Association экспортируется в определенный файл. Поскольку инструкция указывает **с зависимостями**, объекты источника данных и представления источников данных также включаются в ABF-файл.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41; DDL](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)   
 [ИМПОРТ &#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&#41;](../dmx/import-dmx.md)   
 [Экспорт и импорт объектов интеллектуального анализа данных](https://docs.microsoft.com/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
  
