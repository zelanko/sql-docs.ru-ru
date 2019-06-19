---
title: Элемент DropOnlyMode (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1d449defa98112c87a4b5789f1cff6f764252e3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62659582"
---
# <a name="droponlymode-element-dta"></a>Элемент DropOnlyMode (DTA)
  Указывает, что помощник по настройке ядра СУБД должен в ходе сеанса настройки учитывать только возможность удаления существующих индексов, индексированных представлений или секций. При задании этого параметра настройки никакие новые структуры физического проектирования не рассматриваются.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необязательный параметр. Может использоваться только один раз для каждого элемента `TuningOptions`. Не может использоваться, если в элементе `TuningOptions` указаны следующие элементы:<br /><br /> [Элемент FeatureSet (DTA)](featureset-element-dta.md)<br /><br /> [Элемент Partitioning (DTA)](partitioning-element-dta.md)<br /><br /> [Элемент KeepExisting (DTA)](keepexisting-element-dta.md) имеет значение **ВСЕ**|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](tuningoptions-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере показан раздел `TuningOptions` входного XML-файла помощника по настройке ядра СУБД, в котором указано ключевое слово `DropOnlyMode`. В данном примере время настройки ограничено 24 часами (1 440 минутами), а для всех существующих кластеризованных и некластеризованных индексов будет рассматриваться возможность их удаления.  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
