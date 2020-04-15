---
title: Имена корреляций Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dfe0655ace4bbd622dfb80b833f49562732394e2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280964"
---
# <a name="correlation-names"></a>Корреляционные имена
Имена корреляций полностью поддерживаются, в том числе в таблице списка. Например, в следующей строке E1 — это имя корреляции для таблицы под названием Emp:  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```
