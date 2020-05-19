---
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
ms.openlocfilehash: 06d3234317e38177defeacdf6f258bc2301dde9e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747051"
---
# <a name="affectenum"></a>AffectEnum
Указывает, какие записи затрагиваются операцией.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|Если к **набору записей**не применен [Фильтр](../../../ado/reference/ado-api/filter-property.md) , затрагивает все записи.<br /><br /> Если для свойства **Filter** задано строковое условие (например, "author = ' Иванов '"), операция затрагивает видимые записи в текущей главе.<br /><br /> Если для свойства **Filter** задан элемент [филтерграупенум](../../../ado/reference/ado-api/filtergroupenum.md) или массив закладок, операция повлияет на все строки **набора записей**. **Примечание. адаффекталл** скрывается в обозревателе объектов Visual Basic.|  
|**адаффекталлчаптерс**|4|Затрагивает все записи во всех соседних главах **набора записей**, включая те, которые не видны через применяемый в данный момент **Фильтр** .|  
|**adAffectCurrent**|1|Влияет только на текущую запись.|  
|**adAffectGroup**|2|Затрагивает только те записи, которые соответствуют текущему значению свойства [фильтра](../../../ado/reference/ado-api/filter-property.md) . Для использования этого параметра необходимо задать для свойства **Filter** значение **Филтерграупенум** или массив **закладок** .|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. влияет на. ALL|  
|Адоенумс. влияет на. АЛЛЧАПТЕРС|  
|Адоенумс. влияет на. CURRENT|  
|Адоенумс. влияет на. GROUP|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Метод Delete (объект Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Метод Resync](../../../ado/reference/ado-api/resync-method.md)|[Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|
