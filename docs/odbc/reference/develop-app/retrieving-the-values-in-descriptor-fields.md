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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 43467d19f3f2e576efa0402c4ba513e23da59390
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304325"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значений в полях дескриптора
Приложение может вызвать **SQLGetDescField** для получения одного поля записи дескриптора. **SQLGetDescField** предоставляет приложению доступ ко всем полям дескрипторов, определенным в ODBC, а также к полям, определяемым драйвером.  
  
 **SQLGetDescRec** можно вызвать для получения параметров нескольких полей дескриптора, влияющих на тип данных и хранение данных столбца или параметра.
