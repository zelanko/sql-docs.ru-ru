---
title: "Пространство данных (ADO - синтаксис WFC) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0344190472a9548880e828786bd252bdb17de29b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
## <a name="see-also"></a>См. также:  
 [Объект пространства данных (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)

