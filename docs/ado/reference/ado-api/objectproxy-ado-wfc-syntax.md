---
title: ObjectProxy (ADO - синтаксис WFC) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
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
ms.openlocfilehash: dd42478c8da0cc0eba4471ac46a66ec4a08d5bd5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 Необязательно. Массив объектов, являющихся аргументов для метода на сервере. Типы данных Java автоматически преобразуются в типы данных, подходящий для использования на сервере.
