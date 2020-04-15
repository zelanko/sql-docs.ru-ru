---
title: Рекорд-граф Документы Майкрософт
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
ms.openlocfilehash: 28e503ae4602d87fc9138ed018ee1e95f135ec57
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281820"
---
# <a name="record-count"></a>Число записей
Поле заголовка SQL_DESC_COUNT дескриптора является одноуровневым индексом самой высокой пронумерованные записи, содержащей данные. Это поле не является подсчетом всех столбцов или параметров, которые связаны. При выделении дескриптора начальное значение SQL_DESC_COUNT составляет 0.  
  
 Водитель предпринимает любые действия, необходимые для выделения и поддержания любого хранилища, необходимого для хранения информации о дескрипторе. Приложение явно не указывает размер дескриптора и не выделяет новые записи. Когда приложение предоставляет информацию для дескриптора, число которых превышает значение SQL_DESC_COUNT, драйвер автоматически увеличивает сятвуSQL_DESC_COUNT. Когда приложение отклоняет запись дескриптора с самым высоким числом, драйвер автоматически уменьшает SQL_DESC_COUNT, чтобы содержать число наивысшего оставшегося связанного записи.
