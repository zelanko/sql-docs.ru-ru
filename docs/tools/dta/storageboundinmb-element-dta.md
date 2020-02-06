---
title: Элемент StorageBoundInMB (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: f6d83065a572e2d125b43830653fde5a2298eb2b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75306625"
---
# <a name="storageboundinmb-element-dta"></a>Элемент StorageBoundInMB (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Определяет максимальный размер в мегабайтах, который может быть использован в рекомендациях по настройке помощника по настройке ядра СУБД (для набора индексов и секционирования).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|**Тип данных и длина**|**unsignedInt**, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необязательный параметр. Может быть использован только один раз для элемента **TuningOptions** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)|  
|**Дочерние элементы**|None|  
  
## <a name="remarks"></a>Remarks  
 При настройке нескольких баз данных учитываются рекомендации по пространству всех баз данных. По умолчанию помощник по настройке ядра СУБД принимает минимальный из следующих размеров хранилищ:  
  
-   в 3 раза больше текущего размера необработанных данных, включая общий размер кучи и кластеризованных индексов таблиц;  
  
-   свободное место на всех присоединенных дисках плюс размер необработанных данных.  
  
 В размере хранилища по умолчанию не учитываются некластеризованные индексы и индексированные представления.  
  
 Если значение, предусмотренное для элемента **StorageBoundInMB** , превышает реальное свободное место на диске, помощник по настройке ядра СУБД возвращает ошибку, но продолжает настройку. После завершения настройки можно увеличить место на диске, чтобы реализовать рекомендацию.  
  
## <a name="example"></a>Пример  
  
## <a name="description"></a>Description  
 В следующем примере кода показано, как установить предел в 1 500 мегабайт в качестве максимального места на диске, которое может быть занято согласно рекомендациям.  
  
## <a name="code"></a>Код  
  
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
  
  
