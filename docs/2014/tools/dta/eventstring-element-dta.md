---
title: Элемент EventString (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fe8a7c8ad24c472eb41448f1303ad240a5232c9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048427"
---
# <a name="eventstring-element-dta"></a>Элемент EventString (DTA)
  Задает скрипт рабочей нагрузки [!INCLUDE[tsql](../../includes/tsql-md.md)] непосредственно во входном XML-файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
|attribute|Описание|  
|---------------|-----------------|  
|`Weight`|Необязательный параметр. Задает весовой коэффициент запроса (коэффициент важности) для указанного события. Для указания весового коэффициента используется тип данных `float`. Например, `Weight`="100,01". Минимальное значение, которое можно задать для коэффициента `Weight`, равно 0.|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|`string`, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необходимо наличие одного такого элемента, если не задан никакой другой тип рабочей нагрузки. Для родительского элемента `EventString` необходимо задать дочерний элемент `File`, `Database` или `Workload`, однако одновременно может использоваться только один из них. Например, если рабочая нагрузка задается элементом `EventString`, то нельзя задавать рабочую нагрузку также элементом `File` в том же входном XML-файле.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Workload (DTA)](workload-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с описанием встроенной рабочей нагрузки (DTA)](xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
