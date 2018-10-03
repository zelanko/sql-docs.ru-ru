---
title: DataSpace (ADO — синтаксис WFC) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94a539fb2ba3285bd8bb5c3668879695598725a4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718352"
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO — синтаксис WFC)
**CreateObject** метод **DataSpace** класс задает оба бизнес-объект для обработки клиентских запросов приложения (*progid*) и протокол связи и сервер (*подключения*). **createObject** возвращает [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) объект, представляющий сервер.  
  
## <a name="package-commswfcdata"></a>com.ms.wfc.data пакета  
  
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
