---
title: "Элемент StorageBoundInMB (DTA) | Документы Microsoft"
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
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9be01bd27f8a3ad4a878e8b5340f2a4e0aead79e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="storageboundinmb-element-dta"></a>Элемент StorageBoundInMB (DTA)
  Определяет максимальный размер в мегабайтах, который может быть использован в рекомендациях по настройке помощника по настройке ядра СУБД (для набора индексов и секционирования).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**unsignedInt**, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Необязательно. Может быть использован только один раз для элемента **TuningOptions** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Дочерние элементы**|None|  
  
## <a name="remarks"></a>Замечания  
 При настройке нескольких баз данных учитываются рекомендации по пространству всех баз данных. По умолчанию помощник по настройке ядра СУБД принимает минимальный из следующих размеров хранилищ:  
  
-   в 3 раза больше текущего размера необработанных данных, включая общий размер кучи и кластеризованных индексов таблиц;  
  
-   свободное место на всех присоединенных дисках плюс размер необработанных данных.  
  
 В размере хранилища по умолчанию не учитываются некластеризованные индексы и индексированные представления.  
  
 Если значение, предусмотренное для элемента **StorageBoundInMB** , превышает реальное свободное место на диске, помощник по настройке ядра СУБД возвращает ошибку, но продолжает настройку. После завершения настройки можно увеличить место на диске, чтобы реализовать рекомендацию.  
  
## <a name="example"></a>Пример  
  
## <a name="description"></a>Описание  
 В следующем примере кода показано, как установить предел в 1 500 мегабайт в качестве максимального места на диске, которое может быть занято согласно рекомендациям.  
  
## <a name="code"></a>код  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

