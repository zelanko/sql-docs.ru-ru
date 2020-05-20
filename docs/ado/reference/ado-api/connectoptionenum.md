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
author: rothja
ms.author: jroth
ms.openlocfilehash: fa372f05a80290e907298a0969d9eb9f14355f90
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762605"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Указывает, должен ли метод [открытия](../../../ado/reference/ado-api/open-method-ado-connection.md) объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) возвращаться после установления соединения (синхронно) или до (асинхронно).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Асинхронно открывает подключение. Для определения доступности подключения можно использовать событие [коннекткомплете](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) .|  
|**adConnectUnspecified**|-1|По умолчанию. Синхронно открывает подключение.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|Адоенумс. Коннектоптион. КОННЕКТУНСПЕЦИФИЕД|  
  
## <a name="applies-to"></a>Применяется к  
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
