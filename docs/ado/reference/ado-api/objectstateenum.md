---
description: ObjectStateEnum
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
ms.openlocfilehash: 43e511329ba2b32784718d6edb381e6b7085aeb9
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773913"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Указывает, является ли объект открытым или закрытым, подключением к источнику данных, исполнением команды или извлечением данных.  
  
|Константа|Значение|Описание:|  
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

:::row:::
    :::column:::
        [Свойство State (ADO)](./state-property-ado.md)  
    :::column-end:::
    :::column:::
        [Свойство State (многомерные объекты ADO)](../ado-md-api/state-property-ado-md.md)  
    :::column-end:::
:::row-end:::