---
description: XactAttributeEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 2528c9b7a8cf9eb2918983d90e57ac39e6ee989e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441456"
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
  
## <a name="applies-to"></a>Применение  
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
