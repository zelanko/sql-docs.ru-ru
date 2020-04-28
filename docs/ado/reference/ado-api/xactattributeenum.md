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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67947435"
---
# <a name="xactattributeenum"></a>XactAttributeEnum
Задает атрибуты транзакции для объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адксактабортретаининг**|262144|Выполняет сохранность прерываний, вызывая [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) для автоматического запуска новой транзакции. Не все поставщики поддерживают такое поведение.|  
|**адксакткоммитретаининг**|131072|Сохраняет фиксации, вызывая [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) для автоматического запуска новой транзакции. Не все поставщики поддерживают такое поведение.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Ксактаттрибуте. АБОРТРЕТАИНИНГ|  
|Адоенумс. Ксактаттрибуте. КОММИТРЕТАИНИНГ|  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
