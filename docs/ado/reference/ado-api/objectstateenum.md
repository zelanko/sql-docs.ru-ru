---
title: Обжектстатинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
author: rothja
ms.author: jroth
ms.openlocfilehash: e0b69deb64cc4ea04c007fd3d3328cb4154cc3e8
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242621"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Указывает, является ли объект открытым или закрытым, подключением к источнику данных, исполнением команды или извлечением данных.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адстатеклосед**|0|Указывает, что объект закрыт.|  
|**adStateOpen**|1|Указывает, что объект открыт.|  
|**адстатеконнектинг**|2|Указывает, что объект подключается.|  
|**адстатиксекутинг**|4|Указывает, что объект исполняет команду.|  
|**адстатефетчинг**|8|Указывает, что строки объекта извлекаются.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Обжектстате. CLOSED|  
|Адоенумс. Обжектстате. OPEN|  
|Адоенумс. Обжектстате. подключение|  
|AdoEnums.ObjectState.EXEКУТИНГ|  
|Адоенумс. Обжектстате. получение|  
  
## <a name="applies-to"></a>Применение  
  
|||  
|-|-|  
|||

:::row:::
    :::column:::
        [Свойство State (ADO)](../../../ado/reference/ado-api/state-property-ado.md)  
    :::column-end:::
    :::column:::
        [Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)  
    :::column-end:::
:::row-end:::
