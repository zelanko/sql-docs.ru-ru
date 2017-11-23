---
title: "Элемент DatabaseToConnect (DTA) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 21cf5893c23fda68ed62c1415f54844e60947253
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="databasetoconnect-element-dta"></a>Элемент DatabaseToConnect (DTA)
  Позволяет задать первую базу данных, к которой подключается помощник по настройке ядра СУБД при настройке рабочей нагрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Необязательно. Может использоваться один раз для каждого элемента **TuningOptions** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)|  
|**Дочерние элементы**|None|  
  
## <a name="remarks"></a>Замечания  
 Используйте **DatabaseToConnect** для указания имени первой базы данных, к которой должен подключиться помощник по настройке ядра СУБД при запуске сеанса настройки. Этот элемент позволяет задать только одну базу данных. Если задано несколько имен баз данных, помощник по настройке ядра СУБД вернет ошибку.  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Образец входного XML-файла с описанием встроенной рабочей нагрузки (DTA)](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
