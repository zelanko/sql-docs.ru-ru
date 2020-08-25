---
description: AffectEnum
title: Аффектенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
author: rothja
ms.author: jroth
ms.openlocfilehash: d67a4916328d5d6d435da1b8080be42e52b35f67
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776653"
---
# <a name="affectenum"></a>AffectEnum
Указывает, какие записи затрагиваются операцией.  
  
|Константа|Значение|Описание:|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|Если к **набору записей**не применен [Фильтр](./filter-property.md) , затрагивает все записи.<br /><br /> Если для свойства **Filter** задано строковое условие (например, "author = ' Иванов '"), операция затрагивает видимые записи в текущей главе.<br /><br /> Если для свойства **Filter** задан элемент [филтерграупенум](./filtergroupenum.md) или массив закладок, операция повлияет на все строки **набора записей**. **Примечание. адаффекталл** скрывается в обозревателе объектов Visual Basic.|  
|**адаффекталлчаптерс**|4|Затрагивает все записи во всех соседних главах **набора записей**, включая те, которые не видны через применяемый в данный момент **Фильтр** .|  
|**adAffectCurrent**|1|Влияет только на текущую запись.|  
|**adAffectGroup**|2|Затрагивает только те записи, которые соответствуют текущему значению свойства [фильтра](./filter-property.md) . Для использования этого параметра необходимо задать для свойства **Filter** значение **Филтерграупенум** или массив **закладок** .|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. влияет на. ALL|  
|Адоенумс. влияет на. АЛЛЧАПТЕРС|  
|Адоенумс. влияет на. CURRENT|  
|Адоенумс. влияет на. GROUP|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Метод CancelBatch (ADO)](./cancelbatch-method-ado.md)  
        [Метод Delete (объект Recordset ADO)](./delete-method-ado-recordset.md)  
    :::column-end:::
    :::column:::
        [Метод Resync](./resync-method.md)  
        [Метод UpdateBatch](./updatebatch-method.md)  
    :::column-end:::
:::row-end:::