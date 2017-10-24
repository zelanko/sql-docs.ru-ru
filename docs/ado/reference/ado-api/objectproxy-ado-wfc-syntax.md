---
title: "ObjectProxy (ADO - синтаксис WFC) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0bd3aa2bd2cf7b49432e6b29c312e65819d50f4a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - WFC синтаксис)
**ObjectProxy** объект представляет сервер и возвращается **createObject** метод [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) объекта. Класс ObjectProxy имеет один метод **вызова**, который можно вызвать метод на сервере и вернуть объект, полученный в результате этого вызова.  
  
 **пакет com.ms.wfc.data**  
  
## <a name="methods"></a>Методы  
  
### <a name="call-method-adowfc-syntax"></a>Вызовите метод (ADO и WFC синтаксис)  
 Вызывает метод для сервера, представленных ObjectProxy. При необходимости аргументы метода может быть передан как массив объектов.  
  
#### <a name="syntax"></a>Синтаксис  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>Возвращает  
 Объект  
 Объект, полученный из вызова метода.  
  
#### <a name="parameters"></a>Параметры  
 *ObjectProxy*  
 **ObjectProxy** объект, представляющий сервер.  
  
 *метод*  
 Строка, содержащая имя метода для вызова на сервере.  
  
 *args*  
 Необязательно. Массив объектов, являющихся аргументов для метода на сервере. Типы данных Java автоматически преобразуются в типы данных, подходящий для использования на сервере.

