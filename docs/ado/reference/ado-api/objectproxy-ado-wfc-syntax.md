---
title: ObjectProxy (ADO - синтаксис WFC) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ce52d661b5fffe6f0263baa81808dc7d1e9fd3b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279663"
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
  
 *Метод*  
 Строка, содержащая имя метода для вызова на сервере.  
  
 *args*  
 Необязательный параметр. Массив объектов, являющихся аргументов для метода на сервере. Типы данных Java автоматически преобразуются в типы данных, подходящий для использования на сервере.
