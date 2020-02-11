---
title: Ксактаттрибутинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d828c2b9b49138cc4dfd6345d90e70c333554fe0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947435"
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Задает атрибуты транзакции для объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адксактабортретаининг**|262144|Выполняет сохранность прерываний, вызывая [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) для автоматического запуска новой транзакции. Не все поставщики поддерживают такое поведение.|  
|**адксакткоммитретаининг**|131072|Сохраняет фиксации, вызывая [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) для автоматического запуска новой транзакции. Не все поставщики поддерживают такое поведение.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Ксактаттрибуте. АБОРТРЕТАИНИНГ|  
|Адоенумс. Ксактаттрибуте. КОММИТРЕТАИНИНГ|  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
