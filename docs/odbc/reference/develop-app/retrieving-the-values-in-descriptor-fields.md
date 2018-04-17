---
title: Получение значения в поля дескриптора | Документы Microsoft
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b9b00624f9d327e4c561c2d7272e7459e3ed176
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значения в поля дескриптора
Приложение может вызвать **SQLGetDescField** получить одно поле записи дескриптора. **SQLGetDescField** дает приложению доступ для поля дескриптора, определенные в ODBC с также поля, определяемые драйвером.  
  
 **SQLGetDescRec** можно вызвать для получения значения нескольких полей дескриптора, которые определяют тип данных и хранилища данных столбца или параметра.
