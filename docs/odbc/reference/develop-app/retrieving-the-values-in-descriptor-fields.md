---
description: Получение значений в полях дескриптора
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2118efe58b076287dd75192de679bdb74299435
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494652"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значений в полях дескриптора
Приложение может вызвать **SQLGetDescField** для получения одного поля записи дескриптора. **SQLGetDescField** предоставляет приложению доступ ко всем полям дескрипторов, определенным в ODBC, а также к полям, определяемым драйвером.  
  
 **SQLGetDescRec** можно вызвать для получения параметров нескольких полей дескриптора, влияющих на тип данных и хранение данных столбца или параметра.
