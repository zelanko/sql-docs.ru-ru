---
title: Сопоставление SQLFreeConnect | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLFreeConnect
- SQLFreeConnect function [ODBC], mapping
ms.assetid: 8a844538-93c0-4709-bab6-35c45e771d80
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 062894547aca57ca01ca105f4060f2dcd39e942f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086444"
---
# <a name="sqlfreeconnect-mapping"></a>Сопоставление SQLFreeConnect
Когда приложение вызывает **SQLFreeConnect** через драйвер ODBC *3. x* , вызов метода  
  
```  
SQLFreeConnect(hdbc)   
```  
  
 сопоставлен с  
  
```  
SQLFreeHandle(SQL_HANDLE_DBC,Handle)  
```  
  
 с аргументом *Handle* , имеющим значение в *хдбк*.
