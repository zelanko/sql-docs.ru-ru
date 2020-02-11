---
title: Коннектоптионенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 819fb89d7f8c43e76ba9260a72fafa68084bf880
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933449"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Указывает, должен ли метод [открытия](../../../ado/reference/ado-api/open-method-ado-connection.md) объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) возвращаться после установления соединения (синхронно) или до (асинхронно).  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адасинкконнект**|16|Асинхронно открывает подключение. Для определения доступности подключения можно использовать событие [коннекткомплете](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) .|  
|**адконнектунспеЦифиед**|-1|По умолчанию. Синхронно открывает подключение.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|Адоенумс. Коннектоптион. КОННЕКТУНСПЕЦИФИЕД|  
  
## <a name="applies-to"></a>Применяется к  
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
