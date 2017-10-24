---
title: "Элемент DropOnlyMode (DTA) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fac9ba968a7288b7bb7b9a31f93aeb1b597b7ba7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

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
 **Тип данных и длина**  
  
 **Значение по умолчанию**  
  
 **Периодичность**: необязательно. Может использоваться только один раз для каждого элемента **TuningOptions** . Не может использоваться, если в элементе **TuningOptions** указаны следующие элементы:  
  
-   [Элемент FeatureSet (DTA)](../../tools/dta/featureset-element-dta.md)  
  
-   [Секционирование элемент &#40; DTA &#41;](../../tools/dta/partitioning-element-dta.md)  
  
-   [Элемент KeepExisting (DTA)](../../tools/dta/keepexisting-element-dta.md) имеет значение **ВСЕ**  
  
## <a name="element-relationships"></a>Связи элемента  
 **Родительский элемент**: [элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)  
  
 **Дочерние элементы**  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере показан раздел **TuningOptions** входного XML-файла помощника по настройке ядра СУБД, в котором указано ключевое слово **DropOnlyMode** . В данном примере время настройки ограничено 24 часами (1 440 минутами), а для всех существующих кластеризованных и некластеризованных индексов будет рассматриваться возможность их удаления.  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

