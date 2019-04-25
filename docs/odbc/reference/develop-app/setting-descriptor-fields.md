---
title: Установка полей дескриптора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14724a5cc863074344cfbb02615f0ccff228f04c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447672"
---
# <a name="setting-descriptor-fields"></a>Установка полей дескриптора
Чтобы изменить поля дескриптора, приложение может вызвать **SQLSetDescField**. Некоторые поля доступны только для чтения и не может быть задано. (См. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) описание функции.)  
  
 Запись поля дескриптора задаются с помощью номер записи (*RecNumber*) из 1 или более поздней версии, while поля заголовка дескриптора задаются с помощью записи число 0. Число записей в 0 также используется для задания поля закладку, в соответствии с соглашением, закладок содержащихся в столбце 0. Это может привести впечатление, что поля закладки, содержащиеся в заголовке дескриптора, но это не так. Закладка полей отличаются от полей заголовка.  
  
 При задании поля по отдельности, такое приложение должно соответствовать последовательности, определенной в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). При указании некоторых полей драйвера задать другие поля. Это гарантирует, что дескриптор является всегда можно использовать, когда приложение указанный тип данных. Когда приложение задает поле SQL_DESC_TYPE, драйвер проверяет, что другие поля, указывающие тип правильны и согласуются.  
  
 При сбое вызова функции, указывающую поле дескриптора, содержимое поля дескриптора не определены после вызова функции, завершившейся сбоем.
