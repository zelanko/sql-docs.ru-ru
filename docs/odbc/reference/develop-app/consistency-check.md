---
title: Проверка согласованности Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: edd946ca865cd9d8d2edff2c7bedbb3b2629c97c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299004"
---
# <a name="consistency-check"></a>Проверка согласованности
Проверка согласованности выполняется водителем автоматически всякий раз, когда приложение устанавливает SQL_DESC_DATA_PTR поле APD, ARD или IPD. Всякий раз, когда это поле устанавливается, драйвер проверяет, что значение SQL_DESC_TYPE поля и значения, применимые к SQL_DESC_TYPE поле в той же записи, являются действительными и последовательными.  
  
 Поле SQL_DESC_DATA_PTR IPD обычно не устанавливается; однако приложение может сделать это, чтобы заставить проверку согласованности полей IPD. Значение, на которое устанавливается SQL_DESC_DATA_PTR поля IPD, на самом деле не хранится и не может быть получено по вызову в **S'LGetDescField** или **S'LGetDescRec;** настройка сделана только для того, чтобы заставить проверку согласованности. Проверка согласованности не может быть выполнена на IRD.  
  
 Для получения более подробной информации о проверке согласованности, [см.](../../../odbc/reference/syntax/sqlsetdescrec-function.md)
