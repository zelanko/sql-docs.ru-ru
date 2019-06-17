---
title: Корреляционные имена | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b8a253f9d252beb42080d2085adb962206ebd94
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63232309"
---
# <a name="correlation-names"></a>Корреляционные имена
Полностью поддерживаются корреляционные имена, включая список таблиц. Например в следующей строке E1 является корреляционное имя для таблицы с именем Emp:  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
