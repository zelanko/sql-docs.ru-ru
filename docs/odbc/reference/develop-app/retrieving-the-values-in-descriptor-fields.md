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
ms.openlocfilehash: 55d7017c659ca4d0b8094ed4a665d27c10b355f7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020449"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значений в полях дескриптора
Приложение может вызвать **SQLGetDescField** для получения одного поля записи дескриптора. **SQLGetDescField** дает приложению доступ с дескрипторами полей, определенных в ODBC и также полей, определяемых драйвером.  
  
 **SQLGetDescRec** можно вызвать, чтобы получить параметры нескольких полей дескриптора, которые определяют тип данных и хранение данных столбца или параметра.
