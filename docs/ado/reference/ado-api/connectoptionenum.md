---
description: ConnectOptionEnum
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
ms.openlocfilehash: 71142aac94003987267a6d4a6b30d2c9d17c1bfd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444426"
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
  
## <a name="applies-to"></a>Применение  
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
