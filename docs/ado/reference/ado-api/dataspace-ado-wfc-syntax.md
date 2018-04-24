---
title: Пространство данных (ADO - синтаксис WFC) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 18572b2eb08963b2020808040f8a5a7cc43099f2
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="dataspace-ado---wfc-syntax"></a>Пространство данных (ADO - WFC синтаксис)
**CreateObject** метод **DataSpace** класс задает оба бизнес-объект к обработке клиентских запросов приложения (*progid*) и протокол связи и сервера (*подключения*). **createObject** возвращает [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) объект, представляющий сервер.  
  
## <a name="package-commswfcdata"></a>пакет com.ms.wfc.data  
  
### <a name="constructor"></a>Конструктор  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>Методы  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>Свойства  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>См. также  
 [Объект DataSpace (служба удаленных рабочих столов)](../../../ado/reference/rds-api/dataspace-object-rds.md)
