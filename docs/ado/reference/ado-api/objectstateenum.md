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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 708d146aaa40d873e0a519c860a047d4b1f93161
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931926"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Указывает, является ли объект открытым или закрытым, подключением к источнику данных, исполнением команды или извлечением данных.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адстатеклосед**|0|Указывает, что объект закрыт.|  
|**адстатеопен**|1|Указывает, что объект открыт.|  
|**адстатеконнектинг**|2|Указывает, что объект подключается.|  
|**адстатиксекутинг**|4|Указывает, что объект исполняет команду.|  
|**адстатефетчинг**|8|Указывает, что строки объекта извлекаются.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Обжектстате. CLOSED|  
|Адоенумс. Обжектстате. OPEN|  
|Адоенумс. Обжектстате. подключение|  
|Адоенумс. Обжектстате. исполнение|  
|Адоенумс. Обжектстате. получение|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Свойство State (многомерные объекты ADO)](../../../ado/reference/ado-md-api/state-property-ado-md.md)|[Свойство State (ADO)](../../../ado/reference/ado-api/state-property-ado.md)|
