---
title: Элемент Name описания таблицы (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 16e5145ff3338cb597813e26e480d92aa899a1c7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62657249"
---
# <a name="name-element-for-table-dta"></a>Элемент Name описания таблицы (DTA)
  Позволяет задать имя настраиваемой таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|`string`, от 1 до 255 символов|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Обязательный. Один раз для каждого элемента `Table`.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Table описания схемы (DTA)](table-element-for-schema-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Элемент Server (DTA)](server-element-dta.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
