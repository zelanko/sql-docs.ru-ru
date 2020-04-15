---
title: Картирование S'LFreeConnect (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20da205d53acbebca1fee12134c04f17fb8b2db3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302045"
---
# <a name="sqlfreeconnect-mapping"></a>Сопоставление SQLFreeConnect
Когда приложение вызывает **S'LFreeConnect** через драйвер ODBC *3.x,*  
  
```  
SQLFreeConnect(hdbc)   
```  
  
 отображается до  
  
```  
SQLFreeHandle(SQL_HANDLE_DBC,Handle)  
```  
  
 с *аргументом Ручка* установлен на значение в *hdbc*.
