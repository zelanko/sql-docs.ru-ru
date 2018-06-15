---
title: Получение значения в поля дескриптора | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8284167a27439c65256ee4559210843ec7dcffe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911389"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значения в поля дескриптора
Приложение может вызвать **SQLGetDescField** получить одно поле записи дескриптора. **SQLGetDescField** дает приложению доступ для поля дескриптора, определенные в ODBC с также поля, определяемые драйвером.  
  
 **SQLGetDescRec** можно вызвать для получения значения нескольких полей дескриптора, которые определяют тип данных и хранилища данных столбца или параметра.
