---
title: ГДЕ предложения ограничения | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, WHERE clause limitations
- WHERE clause limitations [ODBC]
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eb7aee3b9ebe957f69b269a4d65414066f317930
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="where-clause-limitations"></a>ГДЕ предложения ограничения
Максимальное число предложений в предложение WHERE является 40.  
  
 Столбцы LONGVARBINARY и LONGVARCHAR можно сравнить с литералами до 255 символов в длину, но нельзя сравнивать с помощью параметров.
