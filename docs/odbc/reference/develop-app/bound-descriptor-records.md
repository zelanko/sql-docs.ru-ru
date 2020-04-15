---
title: Связанные записи дескриптора (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 155ef4951abddc7a73d9d4abfbc45248f33d653c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306311"
---
# <a name="bound-descriptor-records"></a>Связанные записи дескриптора
Когда приложение устанавливает SQL_DESC_DATA_PTR поле записи дескриптора, чтобы оно больше не содержит нулевую величину, запись, как говорят, *связана.*  
  
 Если дескриптор является APD, каждая связанная запись представляет собой связанный параметр. Для параметров ввода приложение должно связать параметр для каждого динамического параметра в отчете S'L перед выполнением оператора. Для параметров вывода приложение не должно связывать параметр.  
  
 Если дескриптор является ARD, который описывает ряд данных базы данных, каждая связанная запись представляет собой связанный столбец.
