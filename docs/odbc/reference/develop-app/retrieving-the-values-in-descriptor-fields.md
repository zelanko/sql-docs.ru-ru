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
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05d05eb20fdfa603748e4819d7f7583c6576a0b8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значения в поля дескриптора
Приложение может вызвать **SQLGetDescField** получить одно поле записи дескриптора. **SQLGetDescField** дает приложению доступ для поля дескриптора, определенные в ODBC с также поля, определяемые драйвером.  
  
 **SQLGetDescRec** можно вызвать для получения значения нескольких полей дескриптора, которые определяют тип данных и хранилища данных столбца или параметра.
