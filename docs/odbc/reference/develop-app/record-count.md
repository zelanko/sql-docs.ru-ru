---
description: Число записей
title: Число записей | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d329ca3638f964244cea8c28f7e07e171887fb9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465674"
---
# <a name="record-count"></a>Число записей
Поле заголовка SQL_DESC_COUNT дескриптора — это Отсчитываемый от единицы индекс записи с наибольшим номером, который содержит данные. Это поле не является счетчиком всех связанных столбцов или параметров. При выделении дескриптора начальное значение SQL_DESC_COUNT равно 0.  
  
 Драйвер выполняет любые действия, необходимые для выделения и обслуживания любого хранилища, необходимого для хранения сведений о дескрипторе. В приложении явно не указывается размер дескриптора и не выделяются новые записи. Когда приложение предоставляет сведения для записи дескриптора, число которых превышает значение SQL_DESC_COUNT, драйвер автоматически повышает SQL_DESC_COUNT. Когда приложение отменяет привязку записи с наибольшим номером в дескрипторе, драйвер автоматически уменьшает SQL_DESC_COUNT, чтобы он содержал число наибольших оставшихся связанных записей.
