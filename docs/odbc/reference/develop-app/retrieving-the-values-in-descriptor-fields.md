---
title: Получение значений в полях дескриптора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae95160a11a965e47845726748c2b9449a819e8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775962"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значений в полях дескриптора
Приложение может вызвать **SQLGetDescField** для получения одного поля записи дескриптора. **SQLGetDescField** дает приложению доступ с дескрипторами полей, определенных в ODBC и также полей, определяемых драйвером.  
  
 **SQLGetDescRec** можно вызвать, чтобы получить параметры нескольких полей дескриптора, которые определяют тип данных и хранение данных столбца или параметра.
