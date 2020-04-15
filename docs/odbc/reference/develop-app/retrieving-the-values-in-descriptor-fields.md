---
title: Получение значений в поле дескриптора (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304325"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Получение значений в полях дескриптора
Приложение может позвонить в **S'LGetDescField,** чтобы получить одно поле дескриптора. **S'LGetDescField** предоставляет приложению доступ ко всем полям дескриптора, определенным в ODBC, а также к полям, определяемым драйверами.  
  
 Для получения параметров нескольких полей дескриптора, влияющих на тип данных и хранение столбцов или параметра, можно вызвать **s'LGetDesccRec.**
