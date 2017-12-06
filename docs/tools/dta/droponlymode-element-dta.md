---
title: "Элемент DropOnlyMode (DTA) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8798a084ab6762781e2445700c0f0e4f51d2f617
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="droponlymode-element-dta"></a>Элемент DropOnlyMode (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Указывает, что помощник по настройке ядра СУБД должен учитывать только возможность удаления существующих индексов, индексированных представлений или секций во время сеанса настройки. При задании этого параметра настройки никакие новые структуры физического проектирования не рассматриваются.  
  
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
  
-   [Элемент Partitioning (DTA)](../../tools/dta/partitioning-element-dta.md)  
  
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
  
  
